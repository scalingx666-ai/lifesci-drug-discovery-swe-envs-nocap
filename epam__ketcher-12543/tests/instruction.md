# Issue

**Title:** #12277 - Refactor: Explicit/implicit Any type clean up from packages\ketcher-react\src\script\editor\tool\helper\locate.ts file

## Description

## Summary

Removes every explicit and implicit `any` from `locate.ts` (rectangle and lasso selection) and drops its `no-explicit-any` eslint-disable.

```diff
- function getElementsInRectangle(restruct: ReStruct, p0, p1) {
+ function getElementsInRectangle(restruct: ReStruct, p0: { x: number; y: number }, p1: { x: number; y: number }) {

- restruct.rxnArrows.forEach((item: any, id) => {
-   if (item.item.center().x > x0 && ...
+ restruct.rxnArrows.forEach((_item, id) => {
+   const center = struct.rxnArrows.get(id)?.center();
+   if (center && center.x > x0 && ...

- restruct.enhancedFlags.forEach((item: any, id) => {
+ restruct.enhancedFlags.forEach((item: ReEnhancedFlagWithPosition, id) => {

- const r: any = [];
+ const r: Vec2[] = [];

- function isPointInPolygon(r, p) {
+ function isPointInPolygon(r: Vec2[], p: Vec2) {
```

- `ReRxnArrow.item` is typed with a local `Arrow` type that has no `center()`, so the arrow is now read from `struct.rxnArrows`, where `RxnArrow` has `center()`. It is the same object, and `center()` is now called once instead of four times.
- `ReEnhancedFlag` has no `pp` in its type, so a local `ReEnhancedFlag & { pp?: Vec2 }` keeps the existing check unchanged.

## Evidence

- **Before:** `locate.ts` had `/* eslint-disable @typescript-eslint/no-explicit-any */`, 4 explicit `any`, and untyped `p0`, `p1`, `rr`, `r`, `p` and `hasCurrentRayCrossing`.
  **After:** No `any` left. `tsc --noEmit` (ketcher-react) passes, eslint and prettier pass, and Jest `src/script/editor` passes 120/120.


## Merge Danger

Two-way door. Only internal types change. There is no change to KET/MOL output, public API, or local storage, so it is easy to revert.

  

Memory bank: not needed

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e12e8e9d03d0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.