# Issue

**Title:** Add --template option to generate

## Description

Changes made in this pull request:
- Added `mdbenchmark generate --template` and `mdbenchmark generate -t` as a new default for `mdbenchmark generate --host`. The latter still works.


PR Checklist
------------
 - [x] Added changelog fragment in  `./changelog/` ([more information](https://github.com/bio-phys/MDBenchmark/blob/master/DEVELOPER.rst#using-towncrier))?
 - [x] Issue raised/referenced?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `50c5d1811539`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.