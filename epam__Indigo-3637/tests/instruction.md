# Issue

**Title:** Backmerge: #3636 - Add coordinates support in bingo-nosql

## Description

Use icm/icr saver instead of cmf/crf. Added backward compatibility code.

## Generic request
- [ ] PR name follows the pattern `#1234 – issue name`
- [ ] branch name does not contain '#'
- [ ] base branch (master or release/xx) is correct
- [ ] PR is linked with the issue
- [ ] task status changed to "Code review"
- [ ] code follows product standards
- [ ] regression tests updated

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `320235bc67c3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.