# Issue

**Title:** #12315 - Refactor: no-undef rule violation clean up from packages\ketcher-react\src\script\editor\Editor.ts file

## Description

## Summary

Removes the file-level `/* eslint-disable no-undef */` from `Editor.ts`. It was hiding 3 references to the bare `paper` type namespace in the merged-hover block of `setHover`: the file imports Paper.js as `paperjs`, so ESLint sees `paper` as undefined. The fix follows the merged #12478 (`hoverPath.ts`, #12313).

```diff
 paperjs.setup(document.createElement('canvas'));
-let combinedPath: paper.PathItem | null = null;
+let combinedPath: InstanceType<typeof paperjs.PathItem> | null = null;
 ...
-const paperPath = paperPathFromSVGElement(element) as
-  paper.Path | paper.CompoundPath | undefined;
+const paperPath = paperPathFromSVGElement(element);
```

- `combinedPath` takes its type from the existing `paperjs` import, as in #12478.
- The cast is removed: since #12478, `paperPathFromSVGElement` already returns `Path | CompoundPath | undefined`.

No ESLint config change, one fewer type assertion.

Possible follow-up (not in this PR): this block duplicates `uniteHoverPaths()` in `ketcher-core/.../restruct/hoverPath.ts`. Reusing it needs a new `ketcher-core` export and has slightly different element-removal semantics.

## Evidence

- **Before:** `/* eslint-disable no-undef */` hid 3 `no-undef` errors (`'paper' is not defined`).
  **After:** ESLint is clean on the file; re-adding `paper.PathItem` makes `no-undef` report `'paper' is not defined`. Prettier, `tsc` (dev and build configs), `npm run test`, `npm run test:types`, `test:circ` pass. The emitted JavaScript is identical to master.

### Verified in the app

Molecules mode, merged hover (`editor.hover({ map: 'merge', … })` over 3 atoms and 2 bonds): the combined outline is drawn as one united path (`render.combinedHover`) and removed on un-hover. No console errors.

## Merge Danger

**Door:** two-way

Type annotations and a type assertion only; no runtime change.

**Blast Radius:** minimal

Limited to the merged-hover block in `Editor.ts`. No change to file formats, public API or saved settings.

---

Memory bank: not needed

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e12e8e9d03d0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.