# Issue

**Title:** #12126 - Mark as leaving group option disappears from menu if Undo operation applied

## Description

https://github.com/user-attachments/assets/ef0c3758-f741-43cc-b25b-1bdaa8506454


## What
In the Create Monomer wizard, undoing "Mark as connection point" now restores the atom's potential leaving atoms, so its leaving atom (e.g. the H) offers "Mark as leaving group" again.

## Why
`AssignAttachmentAtomOperation.execute()` removes the attachment atom's entry from `potentialAttachmentPoints`, but its inverse was built with `potentialLeavingAtoms: undefined`, so `RemoveAttachmentPointOperation` had nothing to restore. Undo removed R1 and lost the entry, and the context menu only offers "Mark as leaving group" for atoms in that map.

## How
The operation now keeps the removed set and passes it to its inverse, the same way `AssignLeavingGroupAtomOperation` already does. Redo already worked (history re-executes the original operation) and is unchanged. When the attachment atom has only implicit hydrogens there is no entry to keep, and Undo removes the added H as before.

## Verification
- Browser, `C1(CCCCC1)[H]`: Mark as connection point → Undo restores the map entry and H's menu shows "Mark as leaving group" again; Redo restores R1; "Mark as leaving group" → Undo also works; the implicit-H case still adds and removes its H.
- New unit test `AssignAttachmentAtomOperation.test.ts` (perform → undo → redo, as history runs it); fails on master at the Undo step.
- Docker e2e: the 4 popup specs that use "Mark as connection point" (117 tests), no failures, no screenshot changes.
- `npm run test` and `npm run test:types` pass.

## Check list
- [ ] unit-tests written
- [ ] e2e-tests written
- [ ] documentation updated
- [ ] PR name follows the pattern `#1234 – issue name`
- [x] branch name doesn't contain '#'
- [x] PR is linked with the issue
- [ ] base branch (master or release/xx) is correct
- [x] task status changed to "Code review"
- [ ] reviewers are notified about the pull request

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b4d3b6b6403e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.