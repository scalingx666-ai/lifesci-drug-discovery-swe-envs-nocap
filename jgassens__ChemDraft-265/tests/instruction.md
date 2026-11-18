# Issue

**Title:** Record one undo step when an existing text box is edited

## Description

## Summary

Editing an existing text box recorded no undo step. Each keystroke replaced the document in place, and starting or finishing the edit recorded nothing, so the next undo also took back the action before the edit: place Alpha, place Beta, edit Alpha to Alpha123, press undo once, and Beta was gone too. This happened on macOS and Windows.

- **One step per edit.** Opening an existing text box takes a snapshot of the document, the way the atom-label editor already does. Finishing the edit records one "Edit Text" step from that snapshot. Typing and formatting during the edit belong to that step, an edit that ends with nothing changed records nothing, and redo restores the edit.
- **Other actions during an edit checkpoint it.** Any action that records its own undo step while a text box is open (another command, resizing the box, the palette's preview, an assistant write, a typed rotate or stretch value) first records the text changed so far as one "Edit Text" step, then records its own step, and the edit carries on from there; the editor stays open wherever main keeps it open. So undo walks back one action at a time: type, resize, type, click away, and undo reverts the last typing, then the resize, then the first typing. Starting an edit first settles any open palette preview or typed rotate/stretch value. Every way an edit ends (click away or blur, Escape, a tool switch, starting another edit, switching or closing the tab, quitting) records it once and marks the file changed at once. A document-level undo or redo while editing records the edit and then steps back over it; ⌘Z inside the focused editor keeps the editor's own typing undo, as the atom-label editor does.
- **New text is unchanged.** Placing a text and typing into it stays one step. A typed element symbol still becomes an atom when its first edit ends, recorded as its own step after whatever ended the edit, as on main; a forced undo or redo during that first edit skips the conversion so the undo removes the placed text.
- **Table cells** already record their own labelled step; a new test checks that undo reverts only the edited cell.

## Test expectation changes (existing tests)

| Test | Change | Reason |
|---|---|---|
| `apps/desktop/src/textObjectEdit.dom.test.ts`, `mount()` helper | Gains an optional `empty` parameter (default `false`, the old behaviour) | The new repro test starts from an empty page; every existing caller gets the same document as before |

All other test changes only add tests.

## Tests run

On macOS, at `6b253362` (main at `3ee24107` merged in):

- The 20 test files that touch text editing (3 per command): `MainWindow.textCommit`, `atomLabelEditFocus`, `userFeedbackStress`, `textObjectEdit`, `textEditUndo`, `tableCellEditor`, `MainWindow.canvasFocus`, `MainWindow.textPasteFormatting`, `MainWindow.templateInsert`, `canvasClipboardMenu`, `canvasContextMenu`, `textOnShape`, `isotopeRelabel`, `ringLabelSubstituent.stress`, `MainWindow.plugins`, `App`, `drawingTools`, `editableTarget`, `MainWindow.tabs`, `hoverLabelTyping`: 1,335 tests passed. The repro fails on main on both variants (Beta is deleted at the first undo).
- `git diff --check 224d657f HEAD`: clean
- Full gauntlet at `6b253362`: `pnpm lint` pass; `pnpm vitest run` 586 files passed, 10 skipped, 13,370 tests passed, 28 skipped, 0 failed; `pnpm build` pass; `cargo fmt --check`, `cargo clippy --all-targets -- -D warnings` pass; `cargo test` 648 passed, 9 ignored
- Packaged branch build, built without launching (run-app's own build steps, with the steps that would disturb another running dev build disabled): `app/ChemDraft (dev).app` in the branch worktree, id `org.chemdraft.desktop.dev`, label `fix-text-undo [fix/text-edit-undo]`, stamp `11.01.13.57-codex` at `6b253362`
- The tip `b950fc7e` merges main at `08f82662` (#268, Rust and docs only; only the stamp conflicted); CI judges it
- The tip `cb2ec344` merges main at `d3a65276` (#263). Every file only main changed equals main's. On the merged tree the 20 text-editing test files plus `toolsets.test.ts` and #263's text multi-selection tests pass (1,386 tests); CI judges the rest
- The tip then merges main at `8b118011` (#266, ring placement; only the stamp conflicted); the 20 text-editing test files and #266's placement and layout tests pass on it

An earlier push (`694cde07`) failed CI on two of main's tests that the targeted runs had not included (a resize closed the editor; a second Text-tool placement stopped converting the first); the checkpoint rework fixed both, and every text-editing test file has been run since.

Reviews (agentctl runs; no reviewer reviewed its own model's code):

| Run | Reviewer | Scope | Outcome |
|---|---|---|---|
| run-20261101-134350-026e3f | Opus, high | The repro and the first fix | Core correct. 1 medium: resize, palette preview and assistant writes recorded their own step while a text edit was open, so undo could re-apply the typing. 2 low: a forced undo during a just-placed "N" converted it and then undid only the conversion; no Ctrl+Y or resize-during-edit tests. All fixed |
| run-20261101-134925-065a45 | Opus, low | Those fixes | All three fixed. 1 new medium: during a just-placed text's first edit, a resize or preview ran the auto-conversion inside its own step. Fixed |
| run-20261101-135537-aba516 | Opus, low | That fix | No findings |
| run-20261101-140301-4d75c7 | Astra, low | Merge of main with #260 (`694cde07`; only the stamp conflicted) | No findings: #260's two labelled commits still finish an open text edit first |
| run-20261101-142227-65737c | (sol, writer) | The checkpoint rework after CI | All 20 text-editing files pass |
| run-20261101-143352-0ff27a | Opus, xhigh | The whole change against main at `1dd6daf1` | Linear history in every interleaving tried; 1 medium: an edit started over an open palette or numeric preview recorded a phantom step; 1 low: the quit prompt could miss a text edit's dirty flag. Both fixed in `6b253362` |
| run-20261101-143826-a2eec4 | Astra, low | Merge of main with #264 (only the stamp conflicted) | No findings |
| run-20261101-145009-fc3fc3 | Opus, high | `6b253362` (written by Sonnet) | All findings fixed; two test gaps remain (below) |
| run-20261101-163112-6f4baf | Opus, low | Merge of main with #268 (`b950fc7e`; merged by Sonnet, only the stamp conflicted) | Clean: #268's files equal main's, the branch's files are unchanged |
| run-20261101-182346-b0903c | Opus, high | Merge of main with #263 (`cb2ec344`; merged by Sonnet; #263's multi-box formatting meets this PR's edit-aware formatting in two places, and the test helper `mount()` keeps main's third parameter) | No blocking findings; main's assertions untouched; #263's other changes write only through the checkpointing writers |
| run-20261101-185613-33f00e | Astra, low | Merge of main with #266 (only the stamp conflicted) | No findings; template placement still commits through the checkpointing writers |
| run-20261101-192343-ab0742 | Astra, low | Merge of main with #267 (picture export; only the stamp conflicted) | No findings |

## Platforms

- **macOS and Windows:** shared TypeScript with no platform branch; the DOM tests run both shortcut variants (⌘ on macOS; Ctrl, and the Ctrl+Y redo alternate, on Windows). **Windows hands-on at `6b253362`:** the full runbook (`text-edit-undo.md`, steps 1–10) PASSED: the edit, undo ×3 with Beta kept on the first undo, redo ×3, one step per edit, the unchanged edit, Edit ▸ Undo while editing (undoes the typed character inside the editor, which stays open), the typed `N` that becomes an atom (two undo steps by design, unchanged from main: the first gives back the letter), the table cell, and a real resize drag during an edit (the editor stays open; undo goes back through the last typing, the resize, then the first typing; redo restores all three). An earlier Windows pass at `694cde07` had passed steps 1–6 and 9. **macOS hands-on at `6b253362`:** steps 1–8 PASSED (the edit with Beta kept on the first undo and "Undid Edit Text", redo order, one step per edit, no phantom step for an unchanged edit, Edit ▸ Undo inside the editor, the `N` two-step). Step 9 (table cell) was not run: an empty inserted table collapses to about 25 px on main (a separate table-layout bug from #243, both platforms; the table-cell undo is covered by a DOM test and passed on Windows). Step 10 was partly run: an overlay from another app blocked the resize drag; without the resize, the typing undid as one step and redid. The resize case passed on Windows.

## Known limitations

- Creating a text or an atom this way, and resizing a text box, shows "Undid last document change" in the status, because main records those steps without a label.
- Untested paths: the quit prompt seeing a text edit's dirty flag (needs the desktop quit mocks only `MainWindow.tabs` has), a typed rotate/stretch value applied while a text edit is open (the editor selects only the text, so the app gives no way to reach it), and the palette preview during an edit with a text colour (text colours are not previewable; the test uses a bond colour through the same path).

Build stamp: `11.01.13.57-codex`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cf9d60e1cb61`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.