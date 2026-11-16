# Issue

**Title:** #12310 - Refactor: Explicit/implicit Any type clean up from packages\ketcher-react\src\script\ui\views\toolbars\TopToolbar\TopToolbar.container.ts file

## Description

#12310

## How the feature works? / How did you fix the issue?

Removed the `eslint-disable @typescript-eslint/no-explicit-any`, the explicit `state: any`, and the implicit `any` parameters from `TopToolbar.container.ts`.

- `state` is typed with a local `State` type that describes only the store slices this container reads. Existing types are reused where they fit (`RequestState`, `ToolbarState`, `CustomButton`, `Editor`). The same type is used by `mapStateToProps` and the `getActionState` / `selectCustomButtons` selectors.
- Implicit `any` params are now typed: `actionName: string`, `editor: Editor`, `action: UiActionAction`, `menuName: string, isSelected: boolean` (matching the `onOpen` signature already declared in `ToolbarGroupItem`).
- A local `ActionStatus` type is used instead of the one in `state/action`. That one declares `selected?: boolean`, but for `zoom` the value is a number (`editor.zoom()` in `zoom.js`).
- `currentZoom`: `(selected ?? NaN) * 100` keeps the previous result exactly (`undefined * 100` was already `NaN`). TypeScript doesn't allow arithmetic on `undefined`, so the fallback is now explicit.

No runtime behavior changes. This is a type-only change.

## Check list
- [ ] unit-tests written — not needed, type-only change; full `ketcher-react` test suite passes (79 suites, 597 tests)
- [ ] e2e-tests written — not needed, no behavior change
- [ ] documentation updated — not needed
- [x] PR name follows the pattern `#1234 – issue name`
- [x] branch name doesn't contain '#'
- [x] PR is linked with the issue
- [x] base branch (master or release/xx) is correct
- [ ] task status changed to "Code review"
- [ ] reviewers are notified about the pull request

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e19604f6a020`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.