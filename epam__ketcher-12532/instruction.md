# Issue

**Title:** #12270 - Refactor: Explicit/implicit Any type clean up from packages\ketcher-react\src\script\editor\tool\reactionmap.ts file

## Description

## Summary


Refactored `packages/ketcher-react/src/script/editor/tool/reactionmap.ts` to eliminate explicit and implicit `any` types.

**Diff sketch:**

```diff
- /* eslint-disable @typescript-eslint/no-explicit-any */
- private dragCtx: any;
- private line: any;
+ private dragCtx: ReactionMapDragContext | undefined;
+ private line: ReturnType<Editor['render']['selectionLine']> | null = null;

- constructor(editor)
+ constructor(editor: Editor)

- mousedown(event)
+ mousedown(event: PointerEvent)
```

Also typed `mousemove`, `mouseup`, and `updateLine`, reused the existing `ClosestItemWithMap` and `Vec2` types, and introduced a local `ReactionMapDragContext` interface. Existing reaction-mapping behavior remains unchanged.

## Evidence

- **Before:** The file used explicit `any` types, untyped parameters, and a file-wide ESLint suppression.
- **After:** Target-file ESLint, ESLint with `--no-inline-config`, the React TypeScript check, and `git diff --check` passed. Targeted editor-tool tests passed: **5 suites, 32 tests**.

**Test note:** The full workspace checks reported failures in unrelated React tests involving `isMolfileV2000LimitExceeded` and a Macromolecules TypeScript error involving `CONTENT_LAYOUT_MODE`. The targeted checks for this change passed.

## Merge Danger

**Door:** Two-way

This is a reversible, type-safety refactor with no intended runtime behavior or public API changes.

**Blast Radius:** Narrow

Only `packages/ketcher-react/src/script/editor/tool/reactionmap.ts` was modified.

---



Memory bank: not needed

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3c4418929d96`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.