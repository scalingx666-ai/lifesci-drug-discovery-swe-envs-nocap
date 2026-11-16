# Issue

**Title:** remove support for Python 3.10: remove Python 3.10 tests

## Description

We only want to support the latest three Python version (3.11, 3.12, 3.12). Therefore, the test with Python 3.10 is dropped.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1d6bcda41995`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.