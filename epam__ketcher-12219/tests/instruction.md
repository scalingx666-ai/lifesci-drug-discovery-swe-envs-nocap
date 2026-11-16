# Issue

**Title:** #3725 - Unable to select preset root from rna builder

## Description

## How the feature works? / How did you fix the issue?
(Screenshots, videos, or GIFs, if applicable)

Fixed RNA Builder preset-root selection in both layouts:

* The wide layout now invokes the root selection handler instead of only returning it.
* The compact layout now handles clicks on the root input, so the whole preset becomes active instead of leaving a component selected.
* Added regression coverage for both compact and wide layouts.

https://github.com/user-attachments/assets/407bf24e-6743-476c-b972-e4afb51f3471

## Check list
- [x] unit-tests written
- [ ] e2e-tests written
- [ ] documentation updated
- [x] PR name follows the pattern `#1234 – issue name`
- [x] branch name doesn't contain '#'
- [x] PR is linked with the issue
- [x] base branch (master or release/xx) is correct
- [x] task status changed to "Code review"
- [ ] reviewers are notified about the pull request

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1fd976254e46`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.