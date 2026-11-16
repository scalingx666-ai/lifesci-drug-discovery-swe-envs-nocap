# Issue

**Title:** #12304 - Refactor: Explicit/implicit Any type clean up from `packages\ketcher-react\src\script\ui\views\toolbars\BottomToolbar\BottomToolbar.tsx` file

## Description

## Summary

Removes the `no-explicit-any` disable and the `opts: any` type from `BottomToolbar.tsx`. `BottomToolbar` doesn't read `active` itself. It only forwards it to `TemplatesList`, so the prop now uses `TemplatesList`'s own type instead of a separate, looser copy.

```diff
-import { TemplatesList } from './TemplatesList';
+import { type TemplatesListProps, TemplatesList } from './TemplatesList';
 …
-  active?: {
-    opts: any;
-    tool: string;
-  };
+  active?: TemplatesListProps['active'];
```

```
BottomToolbarContainer ── active ──▶ BottomToolbar ── {...rest} ──▶ TemplatesList (reads active.tool, active.opts.struct)
```

This is independent of #12591 (#12305, the `TemplatesList.tsx` cleanup). When that PR merges, `active.opts.struct` here becomes `Struct` with no extra change.

## Evidence

- **Before:** `BottomToolbar.tsx` starts with `/* eslint-disable @typescript-eslint/no-explicit-any */` and declares `active.opts` as `any`.
  **After:** no `any` left. Full `ketcher-react` test run passes: prettier, stylelint, eslint, `tsc`, circular-deps, and Jest (80 suites, 601 passed, 1 skipped).

Verified in the app: n/a. This is a type-only change with no runtime code changes.

## Merge Danger

**Door:** two-way

Only types change, so the emitted JS is the same. Reverting the commit restores the previous state.

**Blast Radius:** none

`BottomToolbarProps` is used only by `BottomToolbar.container.ts`, which gets `active` from untyped Redux state. It is not part of the package's public API.

---

Memory bank: not needed

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dabb335d256b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.