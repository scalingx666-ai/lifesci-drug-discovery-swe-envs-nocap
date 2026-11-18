# Issue

**Title:** Escape cancels a drag in progress

## Description

## Summary

Pressing Escape while moving objects did nothing: the move landed on release (found while reviewing #124; also on main). Escape now puts everything back where it started, with **no undo entry**; the release that follows does nothing, and the selection is kept. Status: "Move canceled".

The same now applies to resizing, rotating, group transforms, path/arrowhead/gradient handle edits, mechanism-arrow handles, bond gestures, and lasso or marquee selection. Gestures that already cancelled on Escape (placing a bond, template, arrow or chain; drawing a mechanism arrow; freehand drawing; corner radius; projected tilt; measuring) behave as before. Escape still goes first to label editors, the warnings list, menus and dialogs.

## Files changed

- `apps/desktop/src/MainWindow.tsx`: Escape handling for in-progress gestures.
- `apps/desktop/src/graphicPathEdit.dom.test.ts`: regression tests.

## Tests run

- `pnpm lint`: pass
- `pnpm vitest run` (full): 308 files, 6136 tests pass

## Platforms

- macOS and Windows: drag a molecule and a rectangle, press Escape before releasing

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a445c6140b24`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.