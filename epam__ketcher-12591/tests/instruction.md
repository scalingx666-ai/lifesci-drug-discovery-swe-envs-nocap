# Issue

**Title:** #12305 - Refactor: Explicit/implicit Any type clean up from `packages\ketcher-react\src\script\ui\views\toolbars\BottomToolbar\TemplatesList\TemplatesList.tsx` file

## Description

## Summary

Removes the `no-explicit-any` disable and all `any` types from `TemplatesList.tsx`. The template structures come from `data/templates.js`, which builds them with `MolSerializer.deserialize`, so they are `Struct` objects from `ketcher-core`.

```diff
 active?: {
   tool?: string;
   opts: {
-    struct: any;
+    struct: Struct;
   };
 };
 …
-const makeAction = (struct, index): UiAction => ({
+const makeAction = (struct: Struct, index: number): UiAction => ({
```

This follows the same pattern as `AtomsList.tsx` (#12309), where `active.opts` is typed as `{ label: string }`.

## Evidence

- **Before:** `TemplatesList.tsx` starts with `/* eslint-disable @typescript-eslint/no-explicit-any */`. `opts.struct` is `any`, and the `makeAction` parameters are implicit `any`.
  **After:** no `any` left. Full `ketcher-react` test run passes: prettier, stylelint, eslint, `tsc`, circular-deps, and Jest (80 suites, 601 passed, 1 skipped).

Verified in the app: n/a. This is a type-only change with no runtime code changes.

## Merge Danger

**Door:** two-way

Only types change, so the emitted JS is the same. Reverting the commit restores the previous state.

**Blast Radius:** none

`TemplatesListProps` is exported, but only `BottomToolbar` uses it inside `ketcher-react`. It is not part of the package's public API.

---



Memory bank: not needed

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4e6a81d0273b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.