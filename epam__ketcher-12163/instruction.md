# Issue

**Title:** #6413 -  Long bond appears outside visible canvas area after opening a saved file in Flex mode

## Description

## How the feature works? / How did you fix the issue?
(Screenshots, videos, or GIFs, if applicable)

Autozoom after opening a file in Flex/Snake mode scrolled the canvas to the
top-left corner of the bounding box built from monomer positions only.
Bonds that envelope other monomers (e.g. long cyclic bonds) are drawn
outside that area, so they ended up above or left of the visible canvas.

Extend the left/top of the bounding box with the rendered bounds of
polymer bonds before zooming, so the whole structure stays visible.
<img width="851" height="248" alt="Screenshot 2026-10-12 at 08 28 35" src="https://github.com/user-attachments/assets/375b2e2b-839e-4e27-b404-d915eef608b9" />

## Check list
- [ ] unit-tests written
- [ ] e2e-tests written
- [ ] documentation updated
- [ ] PR name follows the pattern `#1234 – issue name`
- [ ] branch name doesn't contain '#'
- [ ] PR is linked with the issue
- [ ] base branch (master or release/xx) is correct
- [ ] task status changed to "Code review"
- [ ] reviewers are notified about the pull request

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5065e12f00e7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.