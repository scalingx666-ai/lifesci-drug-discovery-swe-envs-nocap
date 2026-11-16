# Issue

**Title:** fix(chat): Gemini CatBot hung on first tool call (auto-allow catgo MCP tools)

## Description

**Symptom:** Gemini CLI provider in CatBot hung forever ("处理中… 758s") on the first message that triggered a tool call.

**Root cause:** When Gemini (ACP) calls a CatGo MCP tool it sends `session/request_permission`. The gemini adapter always deferred to the frontend `permissionCallback`; in a popout/standalone window that round-trip never resolves, so the model blocks indefinitely. The Claude adapter auto-allows trusted `catgo_*`/`mcp__catgo__*` tools (`decide_tool_permission`) and Codex bypasses approvals — Gemini was the only adapter missing it.

**Fix:** `buildPermissionOutcome` auto-allows when `decide_tool_permission` says so or the tool title/id is a catgo tool (`"catgo_view (catgo MCP Server)"` / `mcp_catgo_…`), and honours `skipPermissions`. Non-CatGo tools still gate via the frontend.

Verified live via `POST /api/agent/stream agent=gemini` with a `get_state`-forcing prompt: completes in ~12s (auto-allowed → tool runs → reply) instead of hanging.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ca25b4a30560`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.