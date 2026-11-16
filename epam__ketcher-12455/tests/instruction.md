# Issue

**Title:** #12293 - Refactor: Explicit/implicit Any type clean up from `packages…

## Description

#12293

## How the feature works? / How did you fix the issue?

Removed the `eslint-disable @typescript-eslint/no-explicit-any` and both `any` usages from `Modal.tsx`.

The hand-written `modal: { name: string; form: any; prop: any }` type is replaced with `Pick<ModalState, 'name' | 'form' | 'prop'>`. `ModalState` is the existing type from the modal reducer (`state/modal`), and it describes exactly the object that `Modal.container` passes in from the store. No new types were introduced.

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f13df4841a3d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.