# Issue

**Title:** fix: route SDK permission approvals through backend

## Description

## Summary
Fixes a CatBot SDK-agent permission hang where the user clicks "Allow" on a tool permission card, the card appears to be accepted, but the assistant stays stuck on `Thinking...` and does not continue streaming.

This was reproduced by a user and confirmed fixed in a Windows minimal test build.

## Problem
When CatBot uses an SDK-backed provider such as Claude Code, tool permission requests are created by the backend agent bridge. The backend waits for the frontend to call `/api/agent/permission` so the pending permission promise can be resolved and the SDK can continue tool execution.

However, after the user clicked "Allow" / "Allow for session", the frontend card could visually transition, while the backend-side SDK permission request remained unresolved. The result was a stalled conversation: the UI stayed on `Thinking...`, but no further output arrived.

## Root Cause
`ChatPane.svelte` always passed an `onResolve` callback to `PermissionCard`.

`PermissionCard` treats the presence of `onResolve` as the client-direct path. In that mode it resolves an in-browser permission promise and intentionally skips the backend `resolve_permission()` round-trip.

That is correct for client-direct tool execution, where `pb.resolve` exists.

But SDK-agent permission entries do not have `pb.resolve`; they must go through the backend `/api/agent/permission` endpoint. Because `onResolve` was still being passed, SDK permission cards short-circuited the backend resolution path, leaving the SDK waiting forever.

## Fix
Only pass `onResolve` when the permission entry actually has `pb.resolve`.

- Client-direct permissions still use the local `pb.resolve` callback.
- SDK-agent permissions no longer receive `onResolve`, so `PermissionCard` falls back to its existing backend `resolve_permission()` path.
- This lets Claude/SDK permission approvals correctly release the backend pending permission promise and continue streaming.

## User Impact
Before:
- User clicks "Allow".
- Permission card appears handled.
- CatBot remains stuck on `Thinking...`.
- Tool execution never resumes.

After:
- User clicks "Allow".
- SDK backend receives the permission decision.
- Tool execution resumes.
- CatBot continues output normally.

## Verification
User validation:
- A Windows minimal test build containing this fix was sent to the affected user.
- User confirmed the issue is fixed.

Automated / local checks:
```bash
pnpm vitest run src/lib/server/agent-bridge/adapters/__tests__/claude.test.ts

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8e85894d22f8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.