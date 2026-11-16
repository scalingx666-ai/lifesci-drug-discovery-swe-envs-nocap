# Issue

**Title:** #3234 – When the browser height is too low, the initial appearance of the arrow, which is located under the Atoms toolbar, changes

## Description

## How the feature works? / How did you fix the issue?

The right toolbar previously determined its start position by observing the entire atoms/PT group. When this group was partially clipped, the up arrow appeared even though the toolbar was already at the top.

Moved the start observer to a small marker at the beginning of the group that does not affect the layout.

Added a Playwright regression test covering initial arrow visibility, scrolling down and back to the top, and resizing the viewport to remove overflow. The test fails before the fix and passes after it.

## Video

https://github.com/user-attachments/assets/676e249e-60e3-4cb8-a2a3-3315f1c7a87a

## Check list
- [ ] unit-tests written
- [x] e2e-tests written
- [ ] documentation updated
- [x] PR name follows the pattern `#1234 – issue name`
- [x] branch name doesn't contain '#'
- [x] PR is linked with the issue
- [x] base branch (master or release/xx) is correct
- [ ] task status changed to "Code review"
- [x] reviewers are notified about the pull request

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0cc894b4c7ae`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.