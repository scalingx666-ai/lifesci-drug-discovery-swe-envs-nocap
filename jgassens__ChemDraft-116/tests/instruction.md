# Issue

**Title:** Art objects: typed rotation shows its entry box again

## Description

## Summary

Shift + double-click on a selected shape's rotate handle opens the typed rotation entry ("Z rotation entry" in the status line), but no box appeared. Holding Shift also switched the shape to its path-editing handles, and those replaced the transform frame that hosts the entry box. Found on Windows by real input; also on main.

The path-editing handles now stay away while a rotation entry is open. Typed degrees apply with Enter as one **"Rotate art object"** undo entry; Escape cancels. The X/Y (3D) entry works the same way. Molecules are unchanged.

## Files changed

- `apps/desktop/src/MainWindow.tsx`: `!rotationInput` guard on the path-edit handles; undo label for typed art rotation.
- `apps/desktop/src/graphicPathEdit.dom.test.ts`: six regression cases (focus, typed degrees, undo entry, Escape, X/Y).

## Tests run

- `pnpm lint`: pass
- `pnpm vitest run` (full): 306 files, 6116 tests pass

## Platforms

- macOS and Windows: select a rectangle, Shift + double-click its rotate handle, type 30, Enter

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a9bdc0b19fca`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.