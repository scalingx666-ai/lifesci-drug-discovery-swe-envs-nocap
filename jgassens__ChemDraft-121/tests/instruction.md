# Issue

**Title:** Text objects: double-click reopens an existing text for editing again

## Description

## Summary

Double-clicking an existing text object deselected it instead of opening it for editing, so there was no way to edit an existing text. Found on Windows by real input; also on main, and very likely on macOS (it is DOM structure).

**Cause:** the text's `onDoubleClick` sat on an overlay element under the drawn text (f0f6ee2b), and text paint later moved into the page SVG without routing double-clicks to its object (1a483d5f).

- Double-clicks on the drawn text now reach their text object (routed by `data-object-id`, so it also works with #109's layering).
- A Text-tool click on an existing text edits it instead of adding a new one on top.
- **T** reopens a selected text. Enter stays unbound, as before.
- The caret goes to the end of the text (click-to-position mapping is not available yet).

## Files changed

- `apps/desktop/src/MainWindow.tsx`: double-click routing, Text-tool edit, T reopen.
- `apps/desktop/src/textObjectEdit.dom.test.ts` (new), `keyboardShortcuts.test.ts`.

## Tests run

- `pnpm lint`: pass
- `pnpm vitest run` (full): 307 files, 6120 tests pass

## Platforms

- macOS and Windows: double-click an existing text; Text tool on an existing text; select + T

🤖 Generated with [Claude Code](https://claude.com/claude-code)

**Owner decision (2026-10-12):** with a real mouse, double-clicking a closed text reopens it and the browser selects the word under the pointer, so typing replaces that word. The owner chose to keep this, as in most text editors. A Text-tool single click reopens with the caret at the end. The DOM tests run in jsdom, which does not do native word selection, so they check the reopen itself.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `af89fcee5493`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.