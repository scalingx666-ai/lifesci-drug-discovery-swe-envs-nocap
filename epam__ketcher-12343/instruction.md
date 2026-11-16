# Issue

**Title:** #12303 - Refactor: Explicit/implicit Any type clean up from packages\ketcher-react\src\script\ui\views\modal\components\toolbox\RgroupLogic\RgroupLogic.container.ts file

## Description

## What
Removed the explicit `any` and the file-level `eslint-disable @typescript-eslint/no-explicit-any` from `RgroupLogic.container.ts`.

## How
`mapStateToProps` now takes `Pick<StoreState, 'modal'>`. The existing `StoreState` (`state/store.types.ts`) already describes `modal.form`, the only part of the store the container reads. No new types, no casts, no runtime change.

## Verification
- ESLint is clean, and a planted `any` is reported (the rule is active for this file).
- Prettier, ketcher-react `tsc`, `test:circ`, `npm run test` and `npm run test:types` pass.
- The R-Group Logic Condition dialog opens from an R-group label, and changing Occurrence (`>0` → `>1`) applies.

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c785fa2c4dcd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.