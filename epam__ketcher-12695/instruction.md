# Issue

**Title:** #12693 - Editor crashes when hovering a selected Data S-group

## Description

## Summary

Hovering a **selected** Data S-group crashed the editor.
While the S-group is selected, `ReSGroup.drawHover` keeps the hover outline from an earlier hover, which Raphael has already removed (`removed: true`, `attrs: null`). Since d5e6fd6c44, `SGroupDataRender` turned the missing path into `[]`, which got past the `!rectCoords` guard in `calculateMiddleCoordsForRect`, so `rectCoords[0][0]` threw.

This PR brings back the pre-regression behaviour: no tooltip while the S-group is selected, and no crash.

## Evidence

- **Before:** label hovered, `ctrl/A`, atom hovered → blank page, `TypeError: can't access property 0, rectCoords[0] is undefined` (`helpers.ts:16`)


https://github.com/user-attachments/assets/4f19b050-3d1b-4980-bc9c-3351e838c68b



  **After:** same steps, no crash and no console error


https://github.com/user-attachments/assets/119ae76c-95a3-4fef-8770-2415d7a89d08



Tests (`packages/ketcher-react`):

```
helpers.test.ts
  calculateMiddleCoordsForRect([])                  // before: throws  → after: returns []
  calculateMiddleCoordsForRect(rectangle)           // returns the 4 edge midpoints
SGroupDataRender.test.tsx
  hovering = { removed: true, attrs: null }         // before: throws  → after: renders nothing
  hovering with a drawn path                        // shows "mass=12"
```

`npm test` in `ketcher-react` (prettier, stylelint, eslint, tsc, dpdm, jest): 82 suites, 605 tests, all passing.

### Verified in the app

- **Feature:** Data S-group hover tooltip
- **Mode:** Molecules, standalone (example dev server)
- **Result:** Hovering a selected Data S-group no longer crashes, and there is no console error. With the S-group not selected, hovering still shows the `mass=12` tooltip.


## Merge Danger

**Door:** two-way

UI-only rendering guard. No KET/MOL output, public API or saved settings change.

**Blast Radius:** small

Only the Data S-group hover tooltip in molecules mode (`SGroupDataRender`). `calculateMiddleCoordsForRect` has no other callers. Macromolecules mode, file round trips and remote mode are not affected.

---

 

Memory bank: not needed

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `090cf8288dec`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.