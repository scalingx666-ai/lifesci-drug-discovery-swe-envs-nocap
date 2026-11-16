# Issue

**Title:** Publish after all others

## Description

Run publish only if all other completed successfully

## Generic request
- [ ] PR name follows the pattern `#1234 – issue name`
- [ ] branch name does not contain '#'
- [ ] base branch (master or release/xx) is correct
- [ ] PR is linked with the issue
- [ ] task status changed to "Code review"
- [ ] code follows product standards
- [ ] regression tests updated

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `60d6eb3fc462`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.