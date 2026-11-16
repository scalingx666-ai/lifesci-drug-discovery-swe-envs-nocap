# Issue

**Title:** #12300 - Refactor: Explicit/implicit Any type clean up from packages\ketcher-react\src\script\ui\views\modal\components\toolbox\Attach\Attach.container.ts file

## Description

## What
Removed the explicit `any` and the file-level `eslint-disable @typescript-eslint/no-explicit-any` from `Attach.container.ts`.

## How
`mapStateToProps` now takes `Pick<StoreState, 'modal'>`. The existing `StoreState` (`state/store.types.ts`) already describes `modal.form`, the only part of the store the container reads. No new types, no casts, no runtime change.

## Verification
- ESLint is clean, and a planted `any` is reported (the rule is active for this file).
- Prettier, ketcher-react `tsc` and `test:circ` pass; `npm run test` passes.
- The Attachment Points dialog opens from the R-group attachment point tool, and Apply adds the attachment point.

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `65e93b06f47b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.