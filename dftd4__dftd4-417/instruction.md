# Issue

**Title:** Fix actions

## Description

- update setup_python to 3.14
- re-enable OMP for tests (only coverage disables OMP, regression from #383)
- fix Fortran and Python coverage

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1107ea7c7c21`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.