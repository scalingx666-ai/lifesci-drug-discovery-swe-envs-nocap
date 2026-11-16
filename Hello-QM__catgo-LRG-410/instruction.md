# Issue

**Title:** fix: load Claude settings env for agent bridge

## Description

## Summary
Fixes a blank CatBot reply issue when users select the Claude Code provider in the desktop app and rely on Claude Code proxy credentials configured in `~/.claude/settings.json`.

This PR makes the Claude agent bridge load only the `env` map from Claude settings as a fallback, so desktop sidecars can see values such as `ANTHROPIC_BASE_URL` and `ANTHROPIC_AUTH_TOKEN` without requiring users to manually duplicate them into Windows system/user environment variables.

## Problem
Some desktop users configure Claude Code to use a local/API proxy through `~/.claude/settings.json`, for example:

{
  "env": {
    "ANTHROPIC_BASE_URL": "http://127.0.0.1:15721",
    "ANTHROPIC_AUTH_TOKEN": "PROXY_MANAGED"
  }
}

When CatBot uses the Claude Code provider, the request may return no visible error but produce an empty assistant bubble / blank reply. Logs can show symptoms such as the Claude connection closing immediately or no token data being received.

## Root Cause
The CatGo desktop agent sidecar launches independently from the user shell. It inherits OS process environment variables, but it does not automatically inherit the `env` block stored in Claude’s settings files.

At the same time, the Claude adapter intentionally uses `settingSources: []`. This prevents loading global Claude MCP/settings that could conflict with CatGo’s own HTTP MCP bridge, but it also means Claude settings env values are not loaded by the SDK path.

So if proxy/auth configuration only exists in `~/.claude/settings.json`, the spawned Claude CLI cannot see `ANTHROPIC_BASE_URL` / `ANTHROPIC_AUTH_TOKEN`, fails to authenticate/connect, and CatBot ends up with a blank reply.

## Fix
This PR adds a narrow fallback in the Claude adapter:

- Reads `env` from `~/.claude/settings.json`.
- Reads `env` from `~/.claude/settings.local.json`.
- Applies those values to the agent bridge process environment only when the variable is not already set.
- Keeps existing OS/user environment variables authoritative.
- Keeps `settingSources: []`, so CatGo still avoids loading unrelated global Claude settings/MCP configuration.

In short: CatGo now loads Claude settings env, but not the rest of Claude global settings.

## Safety Notes
This intentionally does not enable full Claude settings loading.

Only the `env` object is read, which avoids pulling in user-defined MCP servers or other global Claude Code configuration that could interfere with CatGo’s controlled agent bridge setup.

## Tests
Added unit coverage for the fallback behavior:

- Reads env values from `~/.claude/settings.json`.
- Allows `settings.local.json` to override `settings.json`.
- Does not overwrite explicitly provided process environment variables.

Verified with:

pnpm vitest run src/lib/server/agent-bridge/adapters/__tests__/claude.test.ts

Result:

Test Files  1 passed
Tests       8 passed

Also checked:

git diff --check

No whitespace errors were reported, only Windows CRLF conversion warnings.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `418e698523c8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.