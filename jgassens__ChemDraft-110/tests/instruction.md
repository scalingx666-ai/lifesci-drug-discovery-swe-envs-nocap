# Issue

**Title:** Hover labels: Escape cancels the whole typed label, first letter included

## Description

## Summary

Typing over a hovered atom applies the first letter at once as an element hotkey; the next letters open the label editor. Escape used to restore only the state after that first letter, so on a chain atom **N, M, e, Escape** left an **N** while the status line said "Atom label unchanged" (found on Windows by real input; also on main).

Escape now restores the atom and molecule from before the first letter and removes the hotkey's undo entry: the document, Undo, Redo and the saved/unsaved state are as if nothing had been typed. A single letter on its own is still a committed hotkey; Enter still commits the whole label as one undo entry.

**Cause:** cancellation used the post-hotkey draft baseline and kept the hotkey's undo entry.

## Files changed

- `apps/desktop/src/MainWindow.tsx`: the hover assignment records the pre-first-letter history and file state; a hover-started Escape restores them.
- `apps/desktop/src/hoverLabelTyping.dom.test.ts`, `hoverLabelStress.dom.test.ts`: chain, ring and terminal Escape cases, history and file state, single-letter and Enter commits.
- `apps/desktop/src/openWarnings.dom.test.ts`: the Escape-routing test now expects the unknown atom back as `*`, with its warning listed again.

## Tests run

- `pnpm lint`: pass
- `pnpm vitest run` (full): 306 files, 6125 tests pass

## Platforms

- macOS: packaged build check to follow
- Windows: real-input run to follow

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5b581e4a4963`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.