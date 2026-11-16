# Issue

**Title:** fix(desktop): popout structure windows had no Tauri ACL capability

## Description

## Symptom

Opening a structure in a new window (popout) on desktop showed, ~4s later:

> Update failed: Command plugin:app|version not allowed by ACL

## Root cause

Popout structure windows are created with label `structure-<stamp>` (`desktop/lib/popout-manager.ts`), but `src-tauri/capabilities/default.json` did not include that pattern in its `windows` list — so **no capability matched the popout and every Tauri IPC from it was ACL-denied**. The popout loads the same app root, so `UpdateBanner`'s post-launch `check_for_updates()` → `getVersion()` (`plugin:app|version`) was the first denied call the user sees. The `catgo-reload-structure` event listener ("Window + Overwrite" reuse) was silently dead for the same reason.

## Fix

- `capabilities/default.json`: add `structure-*` to the `windows` list (same pattern as the existing `terminal-*` / `doping-pt-*` entries).
- `UpdateBanner.svelte`: gate the post-launch auto-check on `getCurrentWindow().label === 'main'` — popouts shouldn't each fire a duplicate update check anyway.

## Verification

- `vitest run`: 2043 tests pass (file-level failures identical on main — sandbox network noise).
- Capability JSON validated. ACL takes effect at build time — live confirmation lands with the next desktop build.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `76b3a6b864bc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.