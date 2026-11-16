# Issue

**Title:** Modernise CI

## Description

## Description

Improve CI. Fix #39, fix #40 and fix #42:

* Removed `--long` option from CI (and from `pytest`)
  * Users can specify the additional number of tests to run with `--n-tests` 
* Added GitHub actions for `pytest`
* Remove TravisCI and AppVeyor

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9fbdd6d295dd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.