# Issue

**Title:** Tabs: retry, save or discard tabs that could not be restored

## Description

## Summary

A tab whose saved document could not be read at launch was kept in the session so its data is never lost, but it was never tried again, and the "could not be restored" notice came back on every launch with no way out.

- Carried tabs are now **retried at every launch**; those that open become normal tabs.
- **File > Save Unrestored Tabs…** writes each one's saved document to a file you choose, and drops it from the session only once its file is written.
- **File > Discard Unrestored Tabs…** asks first (listing how many and their names: "Their saved document data will be removed from the session. This cannot be undone." Discard / Cancel), then removes them.
- Both are disabled with "No unrestored tabs" when there are none.
- The launch notice names them: "…; 1 tab could not be restored (File > Save Unrestored Tabs… or Discard Unrestored Tabs…)".

**Held for the owner's look** (new menu items).

## Files changed

- `apps/desktop/src/MainWindow.tsx`, `documentSession.ts`: retry, save, discard, notice.
- `apps/desktop/src/commands.ts`, `appMenu.ts`, `src-tauri/src/lib.rs`: the two File commands on both platforms.
- Tests: `MainWindow.tabs.dom.test.tsx`, `documentSession.test.ts`, `appMenu.test.ts`, `App.test.ts`.

## Tests run

- `cargo fmt --check`, `cargo clippy --all-targets -- -D warnings`, `cargo test` (240 passed) on macOS
- `pnpm lint`, `pnpm vitest run` (306 files, 6126 tests): pass

## Platforms

- macOS and Windows: hands-on check to follow (make an unreadable tab in the session file, relaunch, use both commands)

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3be686f8d1fb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.