# Issue

**Title:** Fix indigo-ci

## Description

Return set-matrix to needs for build_indigo_utils_x86_64 - it needed for matrix
[no-ci]

## Generic request
- [ ] PR name follows the pattern `#1234 – issue name`
- [ ] branch name does not contain '#'
- [ ] base branch (master or release/xx) is correct
- [ ] PR is linked with the issue
- [ ] task status changed to "Code review"
- [ ] code follows product standards
- [ ] regression tests updated

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ac87a52241ac`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.