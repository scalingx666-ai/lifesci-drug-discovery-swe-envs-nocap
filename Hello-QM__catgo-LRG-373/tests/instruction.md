# Issue

**Title:** fix(mcp): address the mounted MCP endpoint with a trailing slash

## Description

## Problem
The backend mounts the HTTP MCP app under `/api/mcp` via `app.mount("/api/mcp", mcp_asgi_app)`. Starlette mounted ASGI sub-apps must be addressed at their mounted root **with a trailing slash** — clients hitting `http://…/api/mcp` (no slash) miss the mount and the MCP endpoint fails to register/respond.

## Fix
Use `/api/mcp/` (trailing slash) everywhere the MCP URL is emitted or documented:
- `server/catgo/routers/mcp_http.py`, `server/catgo/setup_claude.py`, `server/main.py`, `server/catgo/routers/hpc.py` (remote registration)
- `readme.md` / `readme.zh.md` diagrams
- `server/tests/test_setup_claude.py` updated to assert the trailing-slash URL (12/12 pass)

Self-contained; unrelated to the load-into-viewer feature (extracted from that branch into its own PR).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `733aecb853f7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.