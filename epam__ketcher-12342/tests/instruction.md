# Issue

**Title:** #12302 - Refactor: Explicit/implicit Any type clean up from packages\ketcher-react\src\script\ui\views\modal\components\toolbox\Bond\Bond.container.ts file

## Description

## What
Removed the explicit `any` and the file-level `eslint-disable @typescript-eslint/no-explicit-any` from `Bond.container.ts`.

## How
`mapStateToProps` now takes `Pick<StoreState, 'modal'> & Pick<CurrentAppState, 'editor'>`. Both come from `state/store.types.ts`: `StoreState` describes `modal.form`, and `CurrentAppState` (added in #11950) types the `editor` slice as `Editor | null`. Because the store starts with `editor: null`, the flag is read with `?.`. The prop was already optional and defaults to `false`, so behaviour is unchanged.

## Verification
- ESLint is clean, and a planted `any` is reported (the rule is active for this file).
- Prettier, ketcher-react `tsc`, `test:circ`, `npm run test` and `npm run test:types` pass.
- Bond Properties opens on double-click, and changing the type (Single → Double) applies.

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `921f4ed6ff4b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.