# Issue

**Title:** #12269 - Refactor: Explicit/implicit Any type clean up from packages\ketcher-react\src\script\editor\tool\paste.ts file

## Description

## Summary

Removes every explicit and implicit `any` from `paste.ts` and drops its `no-explicit-any` eslint-disable, using existing types where they exist. .

```diff
- private action: any;
- private dragCtx: any;
- private mergeItems: any;
+ private action?: Action | null;
+ private dragCtx?: PasteDragContext;   // new local interface
+ private mergeItems?: MergeItems;      // from template.types.ts
```

- Typed the constructor (`Editor`, `Struct`), `mousedown`/`mousemove` (`PointerEvent`), `setMergeItems`, and the debounced merge helper.
- `idsOfItemsMerged` now returns `undefined` instead of `null` when there is nothing to merge, which `getGroupIdsFromItemArrays` expects.
- `toolsMap` in `index.ts` casts `PasteTool` to `ToolConstructorInterface`, the same way it does for atom, bond and template.

## Evidence

- **Before:** `paste.ts` had `/* eslint-disable @typescript-eslint/no-explicit-any */` and 3 explicit `any` fields.
  **After:** No `any` left. `tsc --noEmit` (ketcher-react) passes, eslint and prettier pass on the changed files, and Jest `src/script/editor/tool` passes 32/32.

## Merge Danger

Two-way door. Only internal types change, with no change to KET/MOL output, public API, or local storage. Easy to revert.

---

 
Memory bank: not needed

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e12e8e9d03d0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.