# Issue

**Title:** The document window reopens where it was left

## Description

## Summary
The config main window was created visible, so at launch `ensure_main_window_visible`'s "already on screen" guard (55759546) skipped restoring the saved frame and never centred: Windows left the window in the OS cascade slot (49 px steps at 200%, diagnosed by the Windows session), and macOS skipped the restore the same way. The main window is now created hidden (`"visible": false`), placed at its saved frame or centred on first launch, then shown. A window that really is on screen (second launch, document opened from Explorer/Finder) keeps its live frame and maximized state.

Show-path audit: startup, session/crash recovery and updater relaunch go setup → ensure_main_window_visible → show; early macOS Opened events queue for setup, later Finder opens and Windows argv opens go through document delivery → ensure; single-instance launches queue before setup or call ensure after; Dock Reopen calls ensure.

## Tests
Four vitest checks (config hidden, decision paths), two Rust tests for the restore/centre/keep decision; manual checklist line added. Local gauntlet: lint, vitest 7281 passed, build, fmt, clippy, cargo test 344 passed.

## Platforms
Windows and macOS hands-on runs pending.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ef6cf97aaea4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.