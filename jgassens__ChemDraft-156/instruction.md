# Issue

**Title:** Windows: plugin panels get a normal-height top resize edge

## Description

The top resize band of a Windows plugin panel was only about one DIP tall (the Windows session measured 0–2 physical px at 200%, against 2 px plus the 11 px shadow band on the other edges). It is now the system's resize-border height for the panel's DPI (`GetSystemMetricsForDpi(SM_CYFRAME) + padded border`), using the existing resize overlay.

- Tao's frame geometry is kept: no caption on Windows 10, a single frame.
- The title strip below the band still drags the panel; corners map to the diagonal resize directions.
- macOS unchanged.

**Reviews:** Sol (rvtopband-20261020: implementation OK, two source-text tests needed updating; fixed), re-check rvtopband2-20261020.
**Tests:** lint, cargo fmt/clippy/334 tests, full vitest (two unrelated timeouts under load passed on rerun).
**Platforms:** Windows hands-on pending.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e7e9e196a28c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.