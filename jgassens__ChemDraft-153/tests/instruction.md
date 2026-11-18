# Issue

**Title:** A tab restored from the session saves to its own file again

## Description

A named tab restored from the saved session could not be saved to its own file: Save (and Save from the optional quit prompt) failed with "forbidden path". File access granted by the open dialog or a launch argument lasts only one run, and nothing renewed it for restored tabs. Found by the Windows session while testing #144; the same restore path is shared with macOS.

- When the native side reads the session file, it renews access for exactly the files the session recorded as tab paths, one file at a time, after validation: absolute, no `.` or `..` components, a document extension, an existing regular file. The frontend gains no way to grant arbitrary paths.
- A recorded path that fails validation keeps the tab's content; Save falls back to Save As with a clear message instead of failing.
- Design notes in `docs/architecture/save-open-and-file-format.md`; a hands-on step in `docs/manual-stress-checklist.md`.

**Reviews:** Astra (rvsessionsave-20261019: one P2, '..' paths, fixed; rvdotdot-20261019 APPROVE).
**Tests:** lint, 7049 vitest, cargo fmt/clippy/320 tests on macOS.
**Platforms:** Windows run pending (Windows session); macOS hands-on pending (screen locked).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e7724e1a5f90`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.