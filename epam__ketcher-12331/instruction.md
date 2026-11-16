# Issue

**Title:** #12263 - Refactor: Explicit/implicit Any type clean up from packages\ketcher-macromolecules\src\typings.d.ts file

## Description

## How the feature works? / How did you fix the issue?
(Screenshots, videos, or GIFs, if applicable)

* Fixed the unknown props errors in SubMenu.tsx by filtering children to valid MenuItem elements and deriving their props type from MenuItem.
* Updated library-update-event.spec.ts so the libraryUpdate handler accepts an optional SDF payload, matching the subscription signature.

## Check list
- [ ] unit-tests written
- [ ] e2e-tests written
- [ ] documentation updated
- [x] PR name follows the pattern `#1234 – issue name`
- [x] branch name doesn't contain '#'
- [x] PR is linked with the issue
- [x] base branch (master or release/xx) is correct
- [ ] task status changed to "Code review"
- [ ] reviewers are notified about the pull request

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `43125c73e15d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.