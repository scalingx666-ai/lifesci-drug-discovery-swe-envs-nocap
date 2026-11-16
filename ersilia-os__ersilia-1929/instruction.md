# Issue

**Title:** Make concurrent sessions safe, including the same model in several terminals

## Description

Each terminal is its own session (`~/eos/sessions/session_<parent PID>`), and several terminals can serve models at once, including **the same model**, each in its own container. The per-session parts already worked:
- `run` and `close` only read their own session's `session.json` and `<model>.pid`.
- Containers have unique names, and `close` stops its own by exact name.

What broke concurrent terminals were actions that reached across sessions. This PR fixes them.

## Changes

| Problem | Fix |
|---|---|
| `clean_temp_dir` deleted **every** `ersilia-*` temp dir on the machine, 3× per `serve` and on every `close`. That broke other terminals' in-flight runs, fetches, and conda/venv server logs. | It removes only the temp dirs this session tracks in `<session>/logs/tmp` (via `make_temp_dir`). The tracking geo-IP helper now deletes its own temp dir. |
| Serving with `--disable-cache` (which every fetch does) **force-removed the shared Redis container**, matched by substring `"redis"`. | The container is left running; the session just doesn't use it. The removal helper is deleted. |
| `~/eos/models.json` kept **one session per model** (first writer wins), and the first `close` of that model removed the entry. `ersilia delete` then deleted the registered session dir, possibly another terminal's live one. | It maps each model to a **list** of sessions. Register appends; `close` removes only its own session. A file lock covers the read-modify-write, writes are atomic, and the old single-string format is still read. |
| `ersilia delete` removed the model's image and **stopped running containers in any terminal**. | It refuses in red while a live session serves the model: `Model X is being served in 1 session (session_123). Run 'ersilia close' there before deleting it.` |
| Orphan cleanup at CLI startup killed pids from a dead session's pid file **without checking for pid reuse**, so it could kill another terminal's server. Concurrent cleanup, or an odd `session_*` name, **crashed the CLI** at import. | Pids whose process started after the pid file was written are skipped. Dirs that vanish mid-cleanup and odd names are tolerated, errors are caught per session, and purged sessions are removed from `models.json`. |
| `clean_before_serving` deleted the session's `.pid` files and killed their pids, but **never stopped the Docker containers** listed in them. Those containers kept running untracked, where no cleanup could find them. | It stops those containers too. They belong to this session only. |
| Container names had only 4 hex characters. `find_free_port` could race with another terminal. | Container names use 8 hex characters. If `docker run` reports the port as taken, serve retries once on a new port, unless the user passed `--port`. |
| Unused model-wide stop code (`DockerManager.stop_containers` and its helpers, `AutoService.clean_docker_containers`, `_stop_all_containers_of_image`) would stop **every** container of a model in every terminal, plus a global `docker container prune -f`, if reconnected. `DockerImageService.close` called the nonexistent `self.df`. | The dead code is removed. `DockerImageService.close` stops only its own container. |

### Stale sessions
A session records **which** model it serves (`session.json`) and **where** it runs (`<model>.pid`: URL and container). The two could disagree, so the CLI contradicted itself:
```
$ ersilia run -i in.csv -o out.csv
  ✖  Process ID file does not exist. Please serve the model first!
$ ersilia serve eos3b5e
  ⚠  Model eos1klk is already being served in this terminal.
  ▪  Close eos1klk and serve eos3b5e instead? [Y/n]
```
This happens when serving fails or is interrupted (the session was opened *before* the server started), or when the model's container is removed outside Ersilia (Docker Desktop, `docker rm`, a Docker restart).
- `Session.served_model()` checks that the recorded model really runs: its `.pid` file exists, and its container (or server process, with the pid-reuse check) is alive. If Docker can't be reached, the record is trusted, so a running container never loses its record.
- `run` and `info`: `⚠ Model eos1klk is no longer running in this terminal (its server stopped).` plus `▪ Serve it again with 'ersilia serve eos1klk'.` The stale record is cleared.
- `close` clears the record: `✓ Model eos1klk closed (it was no longer running).`
- `serve` replaces a stale record without the prompt: `▪ Model eos1klk was no longer running; replacing it.`
- `ErsiliaModel.serve` undoes the session record, stopping any started container and removing the `.pid` file, if serving fails or is interrupted with Ctrl+C.

Tested for real in one session with `eos3b5e`: after removing the container with `docker rm -f`, after deleting the `.pid` file, and with Ctrl+C during `serve` at 1.5 s and 2.5 s. Each time, no record or container was left behind.

### Serving the model that is already served
`ersilia serve eos42ez` in a terminal already serving `eos42ez` asked "Close eos42ez and serve eos42ez instead?". If that model is really running (`served_model()`), `serve` now says `✓ Model eos42ez is already being served in this terminal.` and `▪ It is available at http://127.0.0.1:PORT.` A slug resolves to the same model. A stale record is replaced as above, and a different model still gets the question.

**Unchanged on purpose:** sessions stay keyed by the parent PID, not by terminal. `ersilia fetch` runs `ersilia serve` as a subprocess to produce its example output. With terminal-keyed sessions, that background serve would join the user's session and close the model they're serving.

**Known remaining shared state:** the Redis memory policy is global, so the last `--max-memory` wins.

## Testing
- New `test/test_concurrent_sessions.py` (18 tests, no Docker needed):
  - `clean_temp_dir` leaves other sessions' dirs alone
  - `models.json` handles several sessions per model, deregistration and the old format
  - live-session detection
  - purge skips a recycled pid but kills the recorded server
  - cleanup tolerates odd and vanished entries
  - `delete` refuses while a live session serves the model
  - `clean_before_serving` stops the containers of the pid files it removes
  - `served_model()` in every state; `run`, `info` and `close` recovering from a stale session; a failed or interrupted serve leaving no record
  - serving the already-served model again
- `pytest test --ignore=test/fields`: 97 passed, 2 errors. The 2 errors are the URL-search benchmark tests, which also error on `master`. `test/fields` needs `pyairtable`, which isn't installed here.
- **Two concurrent shells** (separate sessions) with `eos42ez`:
  - Both served (two containers), and both ran with identical output.
  - B closed while A was running: A's run finished, and only B's container was removed.
  - A ran again, then closed: only A's container was removed.
  - No tracebacks.
- **Redis:** with A serving `--enable-cache`, B served `--disable-cache` and closed, and the Redis container stayed up.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f5dade4340e1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.