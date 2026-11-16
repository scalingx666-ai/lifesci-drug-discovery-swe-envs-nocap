# Issue

**Title:** #12489 - Autotests: Introduce the new Fragment selection tool in Molecules mode

## Description

## Summary

Adds Playwright coverage for the Fragment Selection tool in Molecules mode (#12489): its place in the selection tools menu, tooltips, the Shift+Tab hotkey, fragment hover and selection, the restriction on bonds in a cycle, and its behavior in the Monomer Creation Wizard.

```
ketcher-autotests/tests/specs/Chromium-popup/Molecules-editor/
└── fragment-selection-tool.spec.ts   (new, 15 cases)
```

| Cases | What is checked                                                                                                   |
| ----- | ----------------------------------------------------------------------------------------------------------------- |
| 1–3   | Fragment Selection is the last item of the selection tools menu, is absent in Macro mode, tooltip `Fragment Selection (Shift+Tab)` |
| 4, 12 | Shift+Tab activates Fragment Selection and cycles Rectangle → Lasso → Structure → Fragment → Rectangle            |
| 5     | Structure Selection tooltip is `Structure Selection (Shift+Tab)` in Molecules and Macromolecules modes            |
| 6, 9  | Hovering a side of a bond outside a cycle shows arrows and outlines the whole fragment on that side (screenshots) |
| 7, 8  | Hovering a bond in a cycle shows the `not-allowed` cursor and a tooltip that appears after at least 200 ms        |
| 10    | Clicking a side of a bond selects that fragment's atoms and bonds, not the clicked bond (`ketcher.editor.selection()`) |
| 11    | Clicking a bond in a cycle selects nothing                                                                        |
| 13–15 | Monomer Creation Wizard: hover and selection stop at a component already marked as Sugar, exclude the connecting bond, and show gray arrows, the `not-allowed` cursor and a tooltip toward the marked component |

## Evidence

- **Before:** no E2E coverage for the Fragment Selection tool.
  **After:** `fragment-selection-tool.spec.ts` with 15 cases in the `chromium-popup` project; Linux snapshots for the arrows and fragment outlines were added with the spec.

Run: `cd ketcher-autotests && npx playwright test --project=chromium-popup tests/specs/Chromium-popup/Molecules-editor/fragment-selection-tool.spec.ts`

Verified in the app: n/a — the PR adds only E2E tests and does not change the editor.

## Merge Danger

**Door:** two-way

Only a new spec file and its snapshots are added; reverting the PR removes them with no other effect.

**Blast Radius:** none

No product code, KET or MOL output, public API, or saved settings change. The only impact is on the `chromium-popup` E2E run time.

---

Memory bank: not needed

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d08687af03f9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.