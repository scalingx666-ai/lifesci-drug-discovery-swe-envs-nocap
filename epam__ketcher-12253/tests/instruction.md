# Issue

**Title:** #12252 – Create a monomer button becomes disabled if used switched to Macromolecules canvas and back

## Description

## How the feature works? / How did you fix the issue?

Refresh the selection state after restoring the Molecules editor so the “Create a monomer” button updates without an extra canvas click.

Added a regression test checking that the button stays enabled after switching to Macromolecules and back.

## Video

https://github.com/user-attachments/assets/dffe7f89-8cc9-4a51-9acc-f50a549e5bf7

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e9e3e5c1bff0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.