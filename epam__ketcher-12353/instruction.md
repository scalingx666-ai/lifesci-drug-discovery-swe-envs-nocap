# Issue

**Title:** #12279 - Refactor: Explicit/implicit Any type clean up from packages\ketcher-react\src\script\ui\component\view\savebutton.tsx file

## Description

## How the feature works? / How did you fix the issue?
(Screenshots, videos, or GIFs, if applicable)

Updated savebutton.tsx:

* Changed server?: any to server?: unknown.
* Changed the onError argument from any to unknown.
* Removed the explicit-any ESLint suppression.

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `00d1a03063ef`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.