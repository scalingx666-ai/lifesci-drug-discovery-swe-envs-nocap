# Issue

**Title:** Enhance usability when using `--skip-validation`.

## Description

Changes made in this pull request:
- Added new error message when running `mdbenchmark generate [...] --skip-validation` without providing a supported MD engine.


PR Checklist
------------
 - [x] Added changelog fragment in  `./changelog/` ([more information](https://github.com/bio-phys/MDBenchmark/blob/master/DEVELOPER.rst#using-towncrier))?
 - [x] Issue raised/referenced?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `466324d42d6f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.