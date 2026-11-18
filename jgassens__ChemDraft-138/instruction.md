# Issue

**Title:** Windows: Ctrl+W on the last drawing closes it and leaves a blank one

## Description

On Windows, Ctrl+W with only one drawing open did nothing. Owner decision (Oct 13): close that drawing the way any tab close does, then leave a new, empty, untitled drawing, so the keystroke never quits the app.

- With one drawing open, Windows now enables the existing `document.closeTab` command (`enableWindowsLastDocumentCloseAction` in `keyboardShortcuts.ts`, platform passed in per AGENTS.md §1). It uses the same close path as any tab: unsaved changes bring up the save box, **Cancel** keeps the drawing, **Don't Save** discards it, and a fresh Untitled drawing takes its place.
- With several drawings open, nothing changes. macOS ⌘W on the last tab still closes the window, as before.

**Review:** Sol checked the replacement, Cancel and Don't Save, session persistence, the platform parameter and unchanged macOS routing. One finding was **not accepted**: Windows' File ▸ Close Window (the predefined item, Alt+F4) closes the *window*, which on Windows quits after flushing the session (AGENTS.md §1), so unsaved drawings come back on the next launch. That is a different action from closing a drawing, and making it match Ctrl+W was not part of the decision.

**Tests:** simulated Windows (one clean drawing; one dirty drawing with Cancel and Don't Save; several drawings) and simulated macOS (⌘W on the last tab unchanged). `pnpm lint` ✓; `MainWindow.tabs.dom.test.tsx`, `keyboardShortcuts.test.ts`, `App.test.ts`: 384 tests ✓.
**Platforms:** Windows hands-on check to follow. macOS behaviour is unchanged and covered by tests; the Mac screen is locked.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `93b2ed67f4d3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.