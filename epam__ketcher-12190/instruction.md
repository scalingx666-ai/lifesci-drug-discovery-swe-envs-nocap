# Issue

**Title:** #4711 – Preview: When hovering over the scroll bar and scrolling through it, the cursor is displayed differently in the Micro and the Macro mode

## Description

## How the feature works? / How did you fix the issue?
Changed the Macromolecules canvas scrollbar cursor from `pointer` to `default` in `ZoomTool.updateScrollBarAttrs`, matching the Molecules mode behavior.

Manually verified that hovering over the scrollbar in Macromolecules mode displays the default cursor.

## Video

https://github.com/user-attachments/assets/98f02817-5fa7-453a-a08c-fedb04851ceb

## Check list
- [ ] unit-tests written
- [ ] e2e-tests written
- [ ] documentation updated
- [x] PR name follows the pattern `#1234 – issue name`
- [x] branch name doesn't contain '#'
- [x] PR is linked with the issue
- [x] base branch (master or release/xx) is correct
- [ ] task status changed to "Code review"
- [x] reviewers are notified about the pull request

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3c4b73957bfb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.