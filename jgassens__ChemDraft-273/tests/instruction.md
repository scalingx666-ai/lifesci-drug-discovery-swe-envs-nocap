# Issue

**Title:** Keep text typed in a table cell when saving or quitting

## Description

## Summary

Text typed into a table cell, caption or footnote was lost if you saved or quit before leaving the cell. The cell editor kept the typed text in a private draft until the edit finished. Save, the session autosave, export and copy all read a document that did not include that draft, so Save wrote the file without the text and marked it saved. Typing never marked the file as changed, so Quit did not ask and the text was gone. This happens on macOS and Windows, on main since tables shipped (#243).

- **Save, autosave, export and Copy As now include an open cell's text.** The open draft is folded into the document they read, the way an open atom label already is. The cell stays open with its caret after Save, and saving adds no undo step.
- **A changed cell marks the file as changed**, so Quit asks to save.
- **Escape after a Save** (which puts back the cell's old text) marks the file changed again. Escape on an unchanged document that was saved before the edit leaves it saved.
- **Switching or closing a tab** with an open cell commits the cell first. If the cell cannot be committed (for example, at the table's character limit), the tab stays put with the cell open and the status says why; the text is never thrown away.
- **IME composition:** the text typed before the composition is saved; nothing is lost or doubled.

Text boxes were checked the same way (Save, autosave and Quit while editing) and do not lose text on main; no change there.

## Tests

New `apps/desktop/src/tableCellSave.dom.test.tsx` (both platform variants; body cell, caption and footnote): Save from the menu with the cell open, the changed mark and quit prompt, the session autosave, Save then Escape, tab switch and close, a commit that fails at the character limit, Copy As, and history after saving. On main `26faaf37` all 24 original cases fail (the saved, autosaved and quit-flush documents lack the typed text, and the file stays marked saved). No existing test changed.

## Tests run

On macOS: the new file plus the table cell editor, canvas, context menu, Copy As, tabs, atom label focus, text undo, clipboard wiring, text commit and user-feedback stress files (694 tests) pass. `pnpm lint` and `git diff --check`: pass. Full suite: CI.

Reviews (agentctl runs; no reviewer reviewed its own model's code):

| Run | Reviewer | Scope | Outcome |
|---|---|---|---|
| run-20261102-074033-5101dc | Astra, xhigh | The repro and first fix (written by sol) | Two P1s: Save then Escape left the file marked saved; a tab switch lost the draft. Fixed |
| run-20261102-075843-31e7a4 | Astra, xhigh | The whole change after those fixes | One P1 (a failed commit on tab switch discarded the draft) and two P2s (needless changed mark after Escape; Copy As missed the draft). Fixed |
| run-20261102-081812-cebfeb | Astra, high | Those fixes | No findings |
| run-20261102-083919-8f3577 | Astra, low | Copy As adds only an open cell draft, not an open atom label (CI had failed three main tests) | No findings; main's tests unchanged |
| run-20261102-082212-f6f70d | Astra, low | Build stamp and merges of main `01ecf572` (#272) and `778b594b` (#271); only the stamp conflicted | No findings |

## Platforms

Shared TypeScript; the DOM tests run both platform variants. **Windows hands-on at `f36c23bc`** (real input): File ▸ Save with a cell open wrote the typed text, kept the editor open with its caret, and cleared the unsaved mark; reopening showed the text. Closing the window while typing quit without a prompt (Windows closes after saving the session), and relaunch restored the tab with the typed text, which then saved. Found: on Windows, Ctrl+S does nothing while any text editor (cell or text box) has focus; File ▸ Save works. That is a separate, existing issue. macOS: in the release stress run.

## Known limitations

None known.

Build stamp: `11.02.07.58-codex`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b8c2c817e295`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.