# Issue

**Title:** #12324 - Refactor: no-redeclare rule violation clean up from packages\ketcher-react\src\script\ui\component\actionmenu.tsx file

## Description

## What
Removed the file-level `eslint-disable no-redeclare` from `actionmenu.tsx` and the violation it hid.

## How
`interface SharedActionProps` was declared twice with byte-identical bodies (a copy-paste duplicate that TypeScript silently merged). The second declaration is removed; the first, declared before its first use, stays. The resulting type is unchanged, so there is no runtime or type change.

## Note
Nothing in the repo imports this module (`ActionMenu`, `showMenuOrButton`), so it appears to be dead code. Removing it is out of this ticket's scope.

## Verification
- ESLint is clean, and restoring the duplicate makes `no-redeclare` report it (the rule is active for this file).
- Prettier, ketcher-react `tsc`, `test:circ`, `npm run test` and `npm run test:types` pass.

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1a097fcffff9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.