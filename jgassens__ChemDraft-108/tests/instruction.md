# Issue

**Title:** Hover labels: Enter no longer leaves the atom selected for the next hotkey

## Description

## Summary

After a multi-letter label typed over a hovered atom (NMe, or a substituent such as OMe) was committed with Enter, moving the pointer to empty canvas and pressing `c` silently turned that atom into C. Found on Windows by real input; also on main.

**Cause:** hover typing selects the atom so the label editor can open on it, and Enter kept that selection. With nothing hovered, `c` fell back to the selected atom.

**Fix:** a hover-started label edit closed with Enter or Escape restores exactly the selection from before the typing started (nothing, the labelled atom, or other atoms on the same molecule). Label-tool edits and the blur policy are unchanged.

## Files changed

- `apps/desktop/src/MainWindow.tsx`: `startedFromHover` on the atom-label edit state; restore the pre-edit selection on a hover close.
- `apps/desktop/src/hoverLabelStress.dom.test.ts`: six regression tests (three empty-canvas `c` cases that fail before the fix; three pre-selection cases).

## Tests run

- `pnpm lint`: pass
- `pnpm vitest run` (full): 305 files, 6107 tests pass

## Platforms

- macOS: to be verified on the packaged build (hover NMe, Enter, move away, `c`)
- Windows: to be verified by real input

## Known limitations

None known.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9dc912df0ab6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.