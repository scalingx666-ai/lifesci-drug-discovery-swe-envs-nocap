# Issue

**Title:** #12125 – Preview tooltip glitch problem

## Description

* #12125 – Preview tooltip glitch problem

* #12125 - update preview tooltip snapshot

* #12125 – Store no preview instead of an empty monomer preview when it is hidden

## How the feature works? / How did you fix the issue?
(Screenshots, videos, or GIFs, if applicable)

Cherry-pick of #12137 into release/3.20.

Fixes the preview tooltip glitch: a hidden preview is now stored as `undefined` instead of an empty monomer preview, so no leftover position stays on the tooltip.

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `94b3e70f1fbf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.