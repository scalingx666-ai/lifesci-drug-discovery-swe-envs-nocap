# Issue

**Title:** Add new test case and reorganize test files

## Description

This consists of two changes:

1. There was no Travis test for the `mofid.run_mofid` functionality, which caused a broken import statement to go unnoticed. This has now been addressed with a new test case `check_run_mofid.py` that runs with `make test`.

2. I felt that the test Python codes should not be in the same directory as the Python codes actually used in running mofid. Therefore, I created a `mofid/tests` directory and put the two Python test codes there, making sure to update the path in `make test`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b07c76f2c9f0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.