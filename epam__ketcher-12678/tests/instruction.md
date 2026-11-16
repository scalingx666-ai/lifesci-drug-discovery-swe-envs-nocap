# Issue

**Title:** #12290 - Refactor: Explicit/implicit Any type clean up from packages\ketcher-react\src\script\ui\views\AppClipArea.tsx file

## Description

## Summary

Removes both explicit `any` casts and the file-level `eslint-disable` from `AppClipArea.tsx`, so `connect` now checks `ClipArea` against the props that `initClipboard` returns. `ClipAreaProps` is exported from `cliparea.tsx` and reused instead of declaring a new type.

```text
views/AppClipArea.tsx
  connect(null, mapDispatch)(ClipArea)
    mapDispatch: (dispatch: Dispatch) =>
      dispatch(initClipboard) -> ClipAreaProps   // was: dispatch(initClipboard as any)
    ClipArea                                      // was: ClipArea as any
component/cliparea/cliparea.tsx
  export interface ClipAreaProps                  // was: not exported
```

## Evidence

- **Before:** `AppClipArea.tsx` starts with `/* eslint-/no-explicit-any */` and uses `as any` twice.
  **After:** the disable comment and both casts are gone.

```text
$ npx tsc --noEmit -p packages/ketcher-react   -> no er
$ npx eslint AppClipArea.tsx cliparea.tsx      -> no warnings
$ npx jest ui/state/hotkeys ui/component/cliparea
  Tests: 4 passed, 4 total
```

Verified in the app: n/a. The change only touches typess unchanged.

## Merge Danger

**Door:** two-way

Types only, with no change to runtime behavior, KET or ings. `ClipAreaProps` is now exported from an internalmodule, which only adds to the surface.

**Blast Radius:** minimal

One cast remains: `dispatch as unknown as (thunk: typeof initClipboard) => ClipAreaProps`. Redux's `Dispatch` type does not model thunks,
so the cast is needed. Typing `initClipboard`'s `dispatk types would remove it, but that means editing`hotkeys.ts` and is left out of this PR.

---

Memory bank: not needed

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5b93c2a5be47`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.