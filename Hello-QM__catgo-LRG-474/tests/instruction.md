# Issue

**Title:** fix(pty): remote terminal no longer disconnects on vi/full-screen apps

## Description

## Summary

The **remote SSH terminal dropped the connection the instant a full-screen program started** (`vi`/`vim`/`less`/`top`/`tmux`), while `cat` of a UTF-8 file worked. This fixes it in the backend so users don't have to avoid full-screen editors.

## Root cause

The asyncssh PTY session (`server/catgo/routers/pty.py`, `_run_remote_asyncssh_pty`) was opened in asyncssh's **default UTF-8 text mode**. A terminal carries arbitrary bytes — escape sequences, box-drawing, non-UTF-8 payloads — and the first non-UTF-8 byte raised `UnicodeDecodeError` inside `process.stdout.read()`. The read loop treats any read exception as channel death and tears the WebSocket down.

The **local** and **subprocess** PTY paths were already binary-safe (`os.read` → bytes), which is exactly why only the **remote (asyncssh)** terminal broke.

Secondary (real but latent on a single event loop): the handler drove the asyncssh process (`create_process`, `stdout.read`, `stdin.write`, `change_terminal_size`, `close`) **directly on the WebSocket loop**, violating the loop-ownership contract documented in `hpc_connection.py` (rule 4) — asyncssh channel state is loop-private and must not be mutated from a foreign loop (e.g. when a connection is owned by the workflow-engine thread).

## Fix

In `_run_remote_asyncssh_pty`:
- **Binary transport** (`encoding=None`); base64-forward raw bytes, matching the `os.read` paths. This is the immediate fix for the disconnect.
- **Owner-loop affinity**: create / read / write / resize / close now go through `hpc.run_on_owner` / `hpc.stream_on_owner` (the connection's own cross-loop bridges). Zero-cost passthrough on the common single-loop path; correct dispatch when the connection is owned by another loop.
- Encode client input (str) → bytes for the binary stdin.

`pty.py` had not changed since v1.0.1 (2026-05-12); the bug shipped in the initial release.

## Verification

- **Unit tests** — new `server/tests/test_remote_pty_binary.py`, **5/5 pass**: non-UTF-8 output forwards verbatim (the regression), binary-mode open, input-as-bytes, resize routing, clean teardown. Existing terminal/HPC tests unaffected.
- **Live-verified**: ran the fixed backend against **SDSC Expanse** and confirmed **`vi` no longer disconnects** the remote terminal (full-screen render + edit + `:q` with the session intact).

## Scope

Backend-only, confined to `_run_remote_asyncssh_pty` + the new test (`+241/−21`). No change to the local/subprocess PTY paths or the connection pool.

---
🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eef8a5e1c44f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.