# Issue

**Title:** fix(server): stop 500 "Load failed" on workflow run (broken log pipe + CORS-less errors)

## Description

## Symptom

Clicking **Run** on a workflow showed a bare red `Run failed: Load failed` in the WebView — connection indicator green, no diagnosable detail.

## Root cause (two stacked bugs)

**1. Broken log pipe → 500.** The desktop app reuses the backend sidecar across app restarts. When the parent that owns the sidecar's stdout/stderr pipes dies, any later write raises `BrokenPipeError: [Errno 32] Broken pipe`. The `/run` handler's first statement was a bare `print(..., flush=True)`, so **every run 500'd** while `/health` (no writes) stayed green — explaining the "connected but Run dies" symptom. Reproduced live: `POST /api/workflow/<id>/run` → `500 {"detail":"Internal server error: BrokenPipeError: [Errno 32] Broken pipe"}`.

**2. 500s shipped without CORS headers.** The `@app.exception_handler(Exception)` response is emitted by Starlette's `ServerErrorMiddleware`, which sits *outside* `CORSMiddleware`, so it carried no `Access-Control-Allow-Origin`. The browser discarded the body and surfaced only the generic `Load failed` — hiding the real detail from #1. (The existing handler comment claimed to add CORS headers but never did.)

## Fix

- `catgo/io_safe.py` — `BrokenPipeSafeStream` wraps `sys.stdout`/`stderr` at startup so writes/flushes swallow `BrokenPipeError`; a dead log pipe can never break request handling. Wired in `main.py` before `logging.basicConfig`.
- Dropped the two stray debug `print()`s in the workflow router (→ `logger.debug`).
- `catgo/cors_util.py` — `apply_cors_headers` re-attaches the same allow-list + regex match `CORSMiddleware` would have set; wired into `global_exception_handler` so 500s reach the browser intact.

## Verification

- New tests: `test_io_safe.py` (writes/flush survive a dead pipe, guard idempotent, delegates `isatty`), `test_cors_util.py` (allowed origin echoed, disallowed/none omitted, **end-to-end 500 carries the header**). **13 passed.**
- `import main` smoke: app loads, stdout/stderr wrapped, handler wired.
- Live repro fixed: after restarting the backend with the patched code path, `/run` returns `200 started`.
- Pre-existing failures in `test_workflow_engine.py` / `test_expanse_e2e.py` / `test_claude_code_mcp.py` confirmed failing on base `main` too (node-set drift + cluster e2e) — not introduced here.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `27f7f553db54`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.