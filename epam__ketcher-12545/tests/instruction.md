# Issue

**Title:** #12308 - Refactor: Explicit/implicit Any type clean up from packages\ketcher-react\src\script\ui\views\toolbars\RightToolbar\RightToolbar.tsx file

## Description

## Summary

Removes the file-level `no-explicit-any` suppression from `RightToolbar.tsx` and types the two `any` props it was hiding, reusing existing types. No new types, no type assertions.

```diff
-import { AtomsList } from './AtomsList';
+import { type AtomsListProps, AtomsList } from './AtomsList';

 interface RightToolbarProps extends Omit<ToolbarGroupItemProps, 'id' | 'options'> {
   className?: string;
-  active?: {
-    opts: any;
-    tool: string;
-  };
-  freqAtoms: any[];
+  active?: AtomsListProps['active'];
+  freqAtoms: string[];
 }
```

- `active` is only read by `<AtomsList>` (`active?.tool === 'atom'`, `active?.opts.label`), so it now uses the shape `AtomsList` declares, one definition instead of a second hand-written copy. `tool` becomes optional, matching `AtomsList` and the runtime value (`activeTool` can be `null`/`undefined`).
- `freqAtoms` is `state.toolbar.freqAtoms`, already `string[]` in the toolbar reducer, and only feeds `<AtomsList atoms>` (`string[]`).

## Evidence

- **Before:** `/* eslint-disable @typescript-eslint/no-explicit-any */` hid 2 `no-explicit-any` errors in `RightToolbarProps`.
  **After:** ESLint is clean on the file; re-adding `freqAtoms: any[]` makes `no-explicit-any` report it. Prettier, `tsc`, `npm run test`, `npm run test:types`, `test:circ` pass.

### Verified in the app

Right toolbar, molecules mode: clicking **N** highlights the N button; picking **Na** from the Periodic Table adds it to the frequent-atoms list and highlights it; switching to the select tool clears the highlight. No console errors.

## Merge Danger

**Door:** two-way

Type-only change to one component's props; no runtime code changes.

**Blast Radius:** minimal

Limited to the right toolbar's prop types. No change to file formats, public API or saved settings.

---

Memory bank: not needed

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e12e8e9d03d0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.