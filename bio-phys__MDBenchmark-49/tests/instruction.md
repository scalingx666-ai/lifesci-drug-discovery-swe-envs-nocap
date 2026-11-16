# Issue

**Title:** Add validation to module name

## Description

Changes made in this pull request:
- Added check of module name to `mdbenchmark.generate`. When given a module name, we try to find it on the system. Users can skip validation with `--skip-validation`. 
- Added `--skip-validation` option to `mdbenchmark.generate`.
- .

PR Checklist
------------
 - [x] Added unit / integration tests.
 - [x] Added changelog fragment in  `./changelog/` ([more information](https://github.com/bio-phys/MDBenchmark/blob/master/DEVELOPER.rst#using-towncrier))?
 - ~[ ] Issue raised/referenced?~

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bfee8f338aac`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.