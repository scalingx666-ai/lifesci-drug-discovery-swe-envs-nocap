# Issue

**Title:** #12297 - Refactor: Explicit/implicit Any type clean up from packages\ketcher-react\src\script\ui\views\modal\components\process\Miew\Miew.tsx file

## Description

## Summary

Removes the file-level `no-explicit-any` suppression from `Miew.tsx` (the 3D Viewer dialog) and types the three `any`s it was hiding, using types that already exist. No type assertions.

```diff
-const Viewer = lazy(() =>
-  import('miew-react').then((module) => ({
-    default: module.default as unknown as ComponentType<any>,
-  })),
-);
+const Viewer = lazy(() => import('miew-react'));

 type MiewDialogProps = {
-  miewOpts: any;
+  miewOpts: ReturnType<typeof createMiewOptions>;
   ...
-  onOk: (result: any) => void;
+  onOk: (result: unknown) => void;
```

- `miewOpts` is exactly what `miewOptionsSelector` builds and passes to Miew's `setOptions(opts: string | object)`.
- `onOk` only reaches `<Dialog params>`, whose `onOk` is `(result: unknown) => void`.
- `miew-react` ships its own types (`onInit?: (miew: Miew) => void`), so the plain lazy import, the form used before #10001, is typed by the library. The cast is not needed under any current config: ketcher-react `tsc` (dev and build configs), the rollup build, the autotests `tsc` and `test:types` all pass without it. The unused `ComponentType` import is removed.

## Evidence

- **Before:** `/* eslint-disable @typescript-eslint/no-explicit-any */` hid 3 `no-explicit-any` errors in the file.
  **After:** ESLint is clean on the file; re-adding `miewOpts: any` makes `no-explicit-any` report it. Prettier, `tsc`, `build:packages`, `npm run test`, `npm run test:types`, `test:circ` pass.

### Verified in the app

3D Viewer, molecules mode: opening it on `c1ccccc1CCO` loads the lazy viewer and renders the molecule with the configured options (light background, lines mode). Apply becomes enabled after `onInit` and loads the structure back (9 atoms); Cancel closes the dialog. No console errors.

## Merge Danger

**Door:** two-way

Type-only edits plus a simpler lazy-import wrapper; `React.lazy` resolves the same component.

**Blast Radius:** minimal

Limited to the 3D Viewer dialog. No change to file formats, public API or saved settings.

---

Memory bank: not needed

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e12e8e9d03d0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.