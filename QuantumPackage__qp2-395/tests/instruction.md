# Issue

**Title:** TaskServer: fix qp_run hang after failed PUB bind

## Description

## Root cause (two)

1. **The verified incident:** when the PUB socket (`tcp://*:<P+1>`) cannot be bound (two `qp_run` processes pick the same port window `10*(pid mod 2823)+32769`), the pub thread dies leaving its sockets open on the shared ZMQ context. `Zmq.Context.terminate` then deadlocks, and `qp_run` hangs forever at 0% CPU after a successful calculation.
2. **Found while testing:** a concurrent `Lazy.force` of `TaskServer.ip_address` from the `qp_run` main thread and the server thread is a race in the native OCaml runtime (no locking in `force_lazy_block`): the second thread executes the `raise_undefined` placeholder as if it were the thunk and dies with `CamlinternalLazy.Undefined` — a second, silent dead-server death with the same 0% CPU hang.

## Fix

- The port pre-check sockets **become** the real REP (P) / PUB (P+1) sockets, bound up front for the whole life of the process — the binds cannot fail later. P+2..P+9 are only probed and released (the Fortran collector PULL binds P+2). A losing concurrent `qp_run` re-scans `+100` instead of killing the other server.
- `TaskServer.run` takes the pre-bound sockets and the resolved address, which the caller forces exactly once in the main thread (removes the lazy race).
- Legacy path: a PUB bind failure closes the pub thread's own sockets (no `ctx_term` deadlock) and reports the error via `pub_error` — the calculation continues; `qp_run` then exits 1 with a clear message.
- `TaskServer.stop` is bounded by a 30 s poll deadline: a dead server yields "no answer to the Terminate request" instead of hanging.
- A crash in the server thread is reported to stderr with a backtrace instead of dying silently.
- `src/zmq/utils.irp.f`: re-enable `ZMQ_RCVTIMEO` (10 s) in `new_zmq_sub_socket` so distributed slaves stop on a timeout instead of blocking forever.
- New deterministic regression driver `ocaml/test_taskserver_fix.ml` (3 cases); the stale `ocaml/tests/test_task_server.ml` stub is updated to the new `run` signature.

## Tests (LCPQ Ampere cluster, compute node)

- Normal, back-to-back, and **two truly concurrent `qp_run`** processes (the original bug trigger): all exit 0, on distinct port windows.
- The exact incident scenario (PUB port pre-occupied by an external occupier): `run()` now returns after ~57 s with `pub_error` set instead of hanging.
- `stop` against a dead server: fails cleanly after ~31 s.
- Pre-bound run/stop: clean in ~1 s.
- Regression driver: `PASS 1` / `PASS 2` / `PASS 3` on both the 4.14 (cluster) and 5.2 (laptop) toolchains.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c42afcd4aeb5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.