# Issue

**Title:** #12307 - Refactor: Explicit/implicit Any type clean up from packages\ketcher-react\src\script\ui\views\toolbars\LeftToolbar\LeftToolbar.container.ts file

## Description

## What
Removed the explicit `any` (and the file-level `eslint-disable`) and the implicit `any[]` from `LeftToolbar.container.ts`.

## Why it needed more than this file
The `any` hid a type mismatch. The toolbar `status` prop was typed as `Tools` (action definitions, every tool key required), but the store's `actionState` holds per-tool `{ selected?, disabled?, hidden? }` booleans plus `activeTool`, and starts as `null`. Typing only the container would have required `{} as Tools`.

## How
- `store.types.ts`: `StoreState` now describes `actionState` (`ActionStatusesState | null`) and `requestsStatuses` (`RequestState`). `ActionStatus` is exported from the action reducer. `actionState` is described separately from the reducer's internal `ActionState`, because that type's loose string index (which mixes in `activeTool`) is not assignable to the props.
- `toolbar.types.ts`: new `ToolbarStatus = { [key in ToolbarItemVariant]?: ActionStatus }`, used for `status` in `ToolbarGroupItem`, `ToolbarMultiToolItem` and its variants.
- `AtomsList.tsx` and `TemplatesList.tsx` (#12309, #12305) receive the same `status` from the Right/Bottom toolbars, so only their `status` type changed. Their own `any`s are left to those tickets.
- Container: `state` is `Pick<StoreState, 'actionState' | 'toolbar' | 'requestsStatuses'>`, `disableableButtons` is `string[]`, and `opened` gets `?? null` (`ToolbarState` allows `undefined`; `opened` is only compared to tool ids, so behaviour is unchanged).

No casts were added. The existing `as ActionButtonProps['status']` casts are untouched.

## Note
#12084 also edits `StoreState`; whichever merges second will have a small textual conflict there.

## Verification
- ESLint is clean, and a planted `any` is reported (the rule is active for the container).
- Prettier, ketcher-react `tsc`, `test:circ`, `npm run test` and `npm run test:types` pass.
- Browser: tool selection highlight, bond/R-group/shape dropdowns, and disabled states in view-only mode behave as before.
- e2e (Docker): `toolbar`, `toolbar-ui`, `left-toolbar-ui` — 23 of 23 passed.

## Check list
- [ ] unit-tests written
- [ ] e2e-tests written
- [ ] documentation updated
- [x] PR name follows the pattern `#1234 – issue name`
- [x] branch name doesn't contain '#'
- [x] PR is linked with the issue
- [ ] base branch (master or release/xx) is correct
- [x] task status changed to "Code review"
- [ ] reviewers are notified about the pull request

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `27243f2d33eb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.