# Issue

**Title:** #12663 - Refactor: Explicit/implicit Any type clean up from packages\ketcher-react\src\script\ui\views\modal\components\toolbox\FG\RemoveFG.tsx file

## Description

## Summary

`RemoveFG` now uses existing types instead of explicit and implicit `any`.

- `fgIds` uses the existing `RemoveFGParams` type.
- The editor uses the existing `Editor` type; callbacks call `onOk` directly.

## Evidence

```ts
// Before
fgIds: any;
const editor = ...editor as any;

// After
interface RemoveFGProps extends BaseProps, RemoveFGParams {}
const editor = ...editor as Editor;
```

Verified in the app: n/a — no visible behavior changes.

## Merge Danger

**Door:** Two-way

Type annotations and callback wiring are localized to `RemoveFG`.

**Blast Radius:** Local

Memory bank: not needed

<!-- START COPILOT CODING AGENT SUFFIX -->

-

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c508b751fe6a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.