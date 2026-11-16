# Issue

**Title:** #12369 - Set macromolecules mode background to the same shade as molecules mode

## Description

## How the feature works? / How did you fix the issue?
Set the macromolecules canvas background to `#FCFCFC` to match molecules mode. Updated the canvas color in the macromolecules theme and replaced hardcoded renderer label backgrounds with a shared core canvas color constant. Added tests to check that the macromolecules theme, CSS custom property, and renderer color stay aligned with the molecules canvas color.

## Check list
- [x] unit-tests written
- [ ] e2e-tests written
- [ ] documentation updated
- [ ] PR name follows the pattern `#1234 – issue name`
- [x] branch name doesn't contain '#'
- [ ] PR is linked with the issue
- [x] base branch (master or release/xx) is correct
- [ ] task status changed to "Code review"
- [ ] reviewers are notified about the pull request

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cddfcb9cf9e8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.