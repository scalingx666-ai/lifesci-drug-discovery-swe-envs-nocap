# Issue

**Title:** macOS: Quit and Cmd+Q save the session before the app exits

## Description

## Summary

The session autosave waits 800 ms after an edit and the app never asks to save, so quitting straight away loses the last edits. Windows already asks the document window to flush the session before quitting. On macOS, the app menu's **Quit (Cmd+Q)** ended the app directly, so anything drawn in the last moment before Cmd+Q was lost.

Quit and Cmd+Q on macOS now go through the same flush as Windows:
- same label, position and shortcut in the app menu;
- a 3-second limit, after which the app quits anyway;
- a second Cmd+Q quits at once;
- with no document window open, it quits at once.

**Not covered:** Dock > Quit, logout/restart, scripted quit and Tauri restart can't be delayed in this Tauri version (tao 0.35.3 registers only `applicationWillTerminate`), so they behave as before.

## Files changed

- `apps/desktop/src-tauri/src/lib.rs`: custom macOS Quit item routed through `request_quit`; preventable exit requests flush first; tests.
- `apps/desktop/src/window-manager/index.ts`, `MainWindow.tsx`: the flush listener on both platforms; `window-manager/quit-flush.dom.test.ts`.

## Tests run

- `pnpm lint`, `pnpm vitest run` (307 files, 6121 tests): pass
- `cargo fmt --check`, `cargo clippy --all-targets -- -D warnings`, `cargo test` on macOS: pass (8 new quit tests)

## Platforms

- macOS: packaged-build check to follow (edit, Cmd+Q at once, relaunch, edit kept)
- Windows: real-input run to follow (closing the window still flushes and quits)

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0be30cdb7e3f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.