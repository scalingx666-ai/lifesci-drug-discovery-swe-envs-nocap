# Issue

**Title:** Status line: list the warnings a file opened with

## Description

## Summary

**Opening a file said "with N warning(s)" and threw the warnings away.** `openDocumentContents` formatted `opened.warnings.length` into a plain status string and dropped the list. A user could not read what the importer said, nor see which atom or object it meant, and the next action replaced the status text, so even the count was gone. For example, `ten-metals.cdxml` opens with 11 warnings and `invalid-element.cdxml` with 3 (the `Element="119"` atom).

**Now the count stays in the status line and opens a list:**

- **The count.** After a file opens with warnings, the status line keeps a small "11 warnings" (or "1 warning", never "1 warnings") after its text has moved on. File ▸ New or another open drops it, and a file that opens cleanly shows none. The open status text uses the same singular and plural.
- **The list.** Clicking the count opens a list above the status line, in the document window. It is not a native utility window, and it is not modal. Each row gives:
  - the importer's own message, unchanged (the §13 text, e.g. `CDXML atom a2 has Element="119", which names no element; imported as an unknown atom (*).`);
  - what the warning names: *Whole file*, *Molecule (CDXML fragment f1)*, *Atom \* in Molecule (CDXML fragment f1)*, or *2 bonds in …*; if that has since been deleted, the row says so;
  - the warning code, muted, for bug reports. Message text can be selected and copied.
- **Show.** A row's Show button selects the molecule, atom or bond its warning names, with the Select tool, and leaves the list open so you can work through the rest.
- **Command.** A new core command, `view.toggleOpenWarnings` ("Show Open Warnings", category view), backs the count (§10). When the document opened without warnings it is disabled with the reason "This document opened without warnings", and invoking it anyway says so. It is in the shell catalogue, so Customize offers it like the other view commands. There is no native menu item, so the Windows menu is untouched.
- **Focus and Esc** (Esc as revised in `e7962fb`):
  - Clicks on the count, Show and × never take keyboard focus (mousedown is prevented), so tool shortcuts work straight after.
  - The list is not `aria-modal`, so shortcuts also work while it is open.
  - Esc closes the list and does nothing else: a capture-phase listener marks it handled, and the canvas handler skips handled events, so a drag keeps going and the eyedropper or another tool stays. Esc from a keyboard-focused row hands focus back to the count.
  - The list is the last thing Esc reaches. An inline label or text edit, a text field, or an open web menu takes it first, and the list closes on the next Esc (`e7962fb`, from review).
  - With the list closed nothing listens, and Esc works exactly as before.
  - A press outside the list closes it and still does its own job (a chain drag still draws).
- **cdx-compat.** `CompatibilityConversionWarning` gains optional `atomIds` and `bondIds`, like `FlattenWarning`'s. They are filled for:
  - `atom_element_unknown`
  - `aromatic_bond_import_approximation`
  - `bond_order_import_unsupported`
  - `bond_display_unsupported` (both sites)
  - `dashed_single_read_as_dative`

  When the endpoint check later skips a bond, warnings name only the bonds the molecule keeps; a warning about skipped bonds alone is about the molecule (`e7962fb`, from review). No warning text changes. The document's stored `compatibility.warnings` keep code, message and object only, so the schema is unchanged.

**Scope:** open and import warnings only. Out of scope:
- paste, save and export warnings;
- warnings persisted in a saved file;
- the atom-label badge texts, `invalidReason`/`invalidDetail` and `atoms.ts`, which #83 is rewriting. This PR does not touch them.

Expect a `MainWindow.tsx` conflict when #83 lands.

## Tests

- **`apps/desktop/src/openWarnings.test.ts`** (model and command, 7 tests):
  - "1 warning", "2 warnings" and the heading;
  - the report is offered only when it has warnings;
  - the unknown Element is named as "Atom \* in Molecule (CDXML fragment f1)" and selects that atom;
  - the whole file, and a molecule for each of ten-metals' 10 per-molecule warnings;
  - a deleted object or atom gives a "no longer" label and nothing to select;
  - several bonds are counted, keeping only those still there;
  - the command is a view command, disabled with its reason until there are warnings, and in `SHELL_COMMAND_IDS` (Customize).
- **`apps/desktop/src/openWarnings.dom.test.ts`** (jsdom, 11 tests). It renders `MainWindow` and opens the fixtures through the location hash. Clicks and keys are DOM events through the app's own handlers, not the bridge.
  - The count is in the status line and the list has 11 rows with their targets. ARIA: `aria-expanded`, `aria-controls` only while the list exists, and no `aria-modal`.
  - "1 warning" for a text-only CDXML file.
  - Show selects the `*` atom (`data-selected-native-atom-id`) with the Select tool.
  - The mousedowns on the count, Show and × are default-prevented, focus never lands in the list, and `e` switches to the Eraser with the list open and after it closes.
  - Esc from a focused row closes the list, focus returns to the count, and `e` still works.
  - Esc with the list open leaves the eyedropper active; a second Esc leaves the eyedropper as before.
  - Esc with the list open leaves a chain drag running and it commits; with the list closed, Esc cancels a drag as before.
  - A press outside closes the list and the chain drag still draws.
  - New, or a cleanly opening file, removes the count; the command then reports its reason.

  - With the list open, a label hover-typed over the `*` atom ("OM" in the focused editor) is cancelled by the first Esc, leaving the atom O and the list open; the second Esc closes the list.
  - With the File menu and the list both open, the first Esc closes the menu and the second closes the list.

  Each Esc test fails with its condition removed.
- **`packages/cdx-compat/src/index.test.ts`**, `describe("CDXML import warnings name their atoms and bonds")`: the unknown Element, aromatic and unsupported orders, an unsupported display and a dashed single each carry the native atom or bond id. A bond skipped for a missing endpoint is not named: a kept aromatic bond gives `["bond_001"]`, a skipped one gives no `bondIds`. The stored warnings keep only code, message and object.
- **Trusted input in a real browser.** On the web dev server in headless Edge, which is Chromium, the engine WebView2 uses, with CDP `Input.dispatchMouseEvent` and `Input.dispatchKeyEvent`. All 10 checks pass:
  - after clicking the count or Show, `document.activeElement` is `BODY`, never in the list, and `e` switches to the Eraser;
  - Show selects `atom_002` (`*`);
  - Esc closes the list and the eyedropper stays; a second Esc leaves it;
  - at the document window's minimum size, **900×640 CSS px, at device scale 1.25 and 1.5**, the list sits inside the viewport (top 252, bottom 612) and its 11 rows overflow and scroll to the last row.
- `docs/manual-stress-checklist.md` has a new entry for the list.

## Stress

Trusted CDP input in headless Edge, against the web dev server. That is a React development build, so the times are upper bounds. All 16 checks pass, with no page exceptions or console errors.

- **400 molecules, 801 warnings** (400 unknown Element, 400 structure, 1 whole file):
  - import: 203 ms headless;
  - from setting the hash to the count showing: 491–672 ms;
  - click to all 801 rows rendered: 456–527 ms;
  - scrolled to the last row (48,063 px of rows), Show selects its molecule (fragment f399) in 342–444 ms;
  - a pointer move over the canvas costs no more with the list open (161–195 ms per move plus 2 frames) than closed (323–356 ms); the dev-build hover over 400 molecules is what dominates.
- **Second file opened with the 801-row list open:** the count becomes "3 warnings" and the list closes, in 49–134 ms.
- **Show, then Delete, Undo, Show, Redo on the `*` atom:**
  - The first Delete resets `*` to C (existing behaviour), and the row follows live: "Atom C in …".
  - The second Delete removes the atom. The row reads "1 atom no longer in Molecule (CDXML fragment f1)" and its Show is gone.
  - Undo ×2 restores the `*` and its Show, and Show selects `atom_002` again.
  - Redo ×2 removes it again, and Show is gone.
- **Esc ×20, list open, chain tool:** the first Esc closes the list and the rest act as Esc did before (the tool steps back to Select). Esc ×20 with the list closed changes nothing. The list then reopens with its 3 rows.

## Platforms

- **Windows:**
  - `pnpm lint` ✅.
  - All of `apps/desktop`, cdx-compat and the CLI in the heavy slot on `86f423f` (before rebasing onto #78, which touches no app or package code): ✅ 171 files, 2908 passed, 0 failed.
  - Focused re-run on `64b6144` after the rebase ✅.
  - Full `pnpm vitest run` on `e7962fb` in the heavy slot, on a clean tree: ✅ 276 files, 5323 passed, 0 failed.
  - `git diff --check` ✅.
  - The headless-Edge trusted-input pass above ✅.
  - **Still to check on Windows, in the app:** in a small document window at 125% and 150% display scale, the list fits and scrolls, Esc closes it, and tool shortcuts work after clicking it.
- **macOS:** not verified. The change is platform-neutral TypeScript and CSS with no native code. Check the same steps there.

## Gates

- [x] Stress test: the §14 gauntlet on `e7962fb` (lint, full vitest, diff --check; Rust gates in CI, no Rust changed) and the stress pass above
- [ ] Owner hands-on check: Mac (pre-tested by the master session), and the Windows step at 150% on the branch build (`C:\dev\owner-check-90\chemdraft.exe`): minimum-size window, the list fits and scrolls, E switches to the Eraser with the list open, and Esc closes it
- [x] Review: claude-fable `fable-pr90-20261010` APPROVE with two minor findings (Esc ahead of editors and menus; skipped bonds named), both fixed in `e7962fb`; scoped re-review `fable-pr90-rr-20261010` APPROVE (dialogs, the Spin overlay and the patch tray unaffected).
- [ ] macOS check

## Squash-merge message

```
Status line: list the warnings a file opened with

Opening a file reported only "with N warning(s)" and threw the warnings
away. The count now stays in the status line ("1 warning", "11
warnings") and opens a list of each warning's own message, what it names
(the whole file, a molecule by its CDXML fragment, or an atom or bond in
it) and its code; Show selects that molecule, atom or bond. A new view
command, Show Open Warnings, backs it and is disabled with a reason when
a document opened clean. The list is not modal and never takes keyboard
focus; Esc closes it without cancelling a drag or leaving a tool. CDXML
import warnings about particular atoms or bonds now carry their native
ids; warning texts and the stored compatibility record are unchanged.

```

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ce40cfe13969`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.