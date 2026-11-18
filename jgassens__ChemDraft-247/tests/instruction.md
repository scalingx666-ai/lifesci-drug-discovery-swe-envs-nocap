# Issue

**Title:** Keep text formatting when pasting a copied text object

## Description

## Summary

Copying a text object with sub- or superscripts (for example H₂O made with the Text tool and Format) and pasting it back with Cmd/Ctrl+V pasted plain text and lost the formatting ("Pasted editable text"). This predates #234; it goes back to 2026-08-11, when desktop Copy started writing the selection to the native clipboard.

**Why it happened.** On desktop, Copy writes the private ChemDraft flavour (and plain text, when the selection contains text) to the native clipboard. Edit ▸ Paste is a predefined menu item, so Cmd/Ctrl+V reaches the page as the webview's `paste` event. Neither WKWebView (macOS) nor WebView2 (Windows) exposes a natively written custom flavour through that event's DataTransfer, so `handlePaste` saw only the plain text and pasted it. Molecules were unaffected because they carry no plain text, so the event looked empty and the existing native fallback ran.

**The fix** (`handlePaste` and `pasteClipboard` in `MainWindow.tsx`):
- On desktop, keyboard paste now reads the native clipboard first, so the private flavour wins and the formatting is kept.
- A snapshot of the event's DataTransfer is taken synchronously, before anything async. It is the fallback when the native read fails (for example, Windows reports the clipboard in use) or finds nothing usable.
- After that come the last in-app selection, then a specific status: "Paste failed: …" or "Nothing to paste". A failed read never becomes a silent unhandled rejection.
- The web build keeps its DataTransfer path unchanged. Text fields, modal dialogs and canvas text editing still paste natively. The copy path, `clipboard.ts`, Rust code, menus and command IDs are untouched.

## Files changed

- `apps/desktop/src/MainWindow.tsx`: `handlePaste` routes desktop paste to `pasteClipboard(snapshot)`; `pasteClipboard` gains the fallback order and status. Build stamp `10.29.11.00-codex`.
- `apps/desktop/src/MainWindow.textPasteFormatting.dom.test.tsx` (new): every case runs for macOS and Windows, with each platform's real native type names (`public.utf8-plain-text` on macOS, `text/plain` from Windows' `CF_UNICODETEXT` mapping).

## Tests run

- `vitest run` on `MainWindow.textPasteFormatting.dom.test.tsx`, `MainWindow.smilesPaste.dom.test.ts` and `canvasClipboardMenu.dom.test.ts`: **69 passed**.
- The new formatting tests **fail on the previous `MainWindow.tsx`** (d015669c) on both platforms and pass with the fix.
- Covered: sub- and superscript kept; external plain text, SMILES and CDXML; native read rejected (clipboard busy), with and without event content; empty native read preferring the event content over the cached selection; cached selection only when nothing else exists; "Nothing to paste"; a web-written selection applied directly; web-build paths unchanged; right-click Paste with and without a failure; modal open; canvas text object and contenteditable targets left to the editor.
- `git diff --check`: clean.
- Root `pnpm lint` (`tsc -p tsconfig.json --noEmit`): **pass** (at 7aaaab8c).
- Full `vitest run` after merging main (a5cba85c): **489 files passed, 10,155 tests passed, 0 failed** (9 files / 22 tests skipped as usual).
- cargo was not run: this PR changes no Rust code. CI covers it on macOS and Windows.

No existing test expectation was changed.

## Results

All targeted tests pass. Review: Opus, approve with changes (one medium finding: a native read failure was unhandled and an empty read skipped the event content; plus two test gaps), all fixed; Opus re-review approved. `Reviewed-by` lines are in the commit.

## Platforms

- **macOS:** unit-tested only. Hands-on not yet run.
- **Windows: verified.** The Windows session ran the hands-on checklist below at a5cba85c: **all 6 pass**. H₂O and Na⁺ keep their sub-/superscripts, with the status "Pasted ChemDraft selection"; a plain word, a SMILES string, context-menu Paste and in-field pastes all behave correctly. That confirms WebView2 hides the natively written flavour from the paste event. The later commits (main's #245 merged in, plus a test-only update) leave this PR's own change unchanged apart from the build stamp; the macOS check runs on the newer tip, which includes #245.

Hands-on checklist (both platforms, branch build):
1. Text tool: type `H2O`, select the `2`, make it subscript (Format). Select the text object, Cmd/Ctrl+C, then Cmd/Ctrl+V on the canvas. **Expect:** a second H₂O with the 2 still subscript; the status is not "Pasted editable text".
2. Same with a superscript (for example `Na+` with `+` superscript).
3. Copy a plain word from TextEdit (macOS) or Notepad (Windows), Cmd/Ctrl+V on the canvas. **Expect:** an editable text object with that word.
4. Copy `c1ccccc1O` from TextEdit or Notepad, paste. **Expect:** a phenol structure.
5. Right-click the canvas ▸ Paste after step 1's copy. **Expect:** the formatted H₂O again.
6. Paste into a text field (for example the inspector) and while editing a text object on the canvas. **Expect:** ordinary text paste into the field, nothing added to the canvas.

## Known limitations

- External CDXML pasted as text keeps its existing "unsupported format" notice. That is unchanged behaviour, not part of this fix.

## One recommended next task

Run the hands-on checklist above on macOS (Windows passed).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5d3eeced7694`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.