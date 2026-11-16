# Issue

**Title:** #12301 - Refactor: Explicit/implicit Any type clean up from Automap.container.ts

## Description

## Summary

Removes `any` from `Automap.container.ts` and drops the file's `no-explicit-any` eslint-disable. Builds on #12368, which already typed `onOk` with `AutomapRequest`.

| Was | Now |
|---|---|
| `state: any` | `State = Pick<StoreState, 'modal'>` |
| `dispatch: any` | `AppDispatch` (`automap()` is a thunk) |
| `ownProps: any` | `OwnProps = Pick<BaseCallProps, 'onOk'>` (the parent's callback) |
| `formState: state.modal.form` | `state.modal.form as StateProps['formState']` |

The one cast stays at the store boundary. The modal store keeps one generic form result (`Record<string, unknown>`) for every dialog. `Atom.container.ts` does the same since #12368.

## Evidence

`npm run test` in `ketcher-react` passes: prettier, stylelint, eslint, tsc, circular deps (none found), jest (80 suites, 601 passed, 1 skipped).

Before this change, `state: any` hid a type mismatch: `tsc` reports TS2322 (`Record<string, unknown>` is not assignable to `AutomapRequest`) as soon as `state` is typed.

Verified in the app: n/a. This is a type-only change, and the emitted JS is unchanged.

## Merge Danger

Two-way door. Only TypeScript types change, with no runtime change, no public API change, and no KET/MOL output change. Blast radius: the Automap dialog container only.

Memory bank: not needed

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `21e588fce07a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.