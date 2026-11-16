# Issue

**Title:** Improved output capturing and added tests

## Description

Send output to client before the whole cell is calculated. May be triggered by:
1) Exceeding buffer limit
2) Newline symbol in output
3) Some time after no flushing was performed

New and old functionality was covered with tests.
New config parameters were added

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `aebe1332e8a8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.