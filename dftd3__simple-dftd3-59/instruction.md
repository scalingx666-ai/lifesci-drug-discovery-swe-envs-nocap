# Issue

**Title:** Update CI workflow

## Description

- downgrade MacOS version
- add Python 3.11 and 3.12 for testing
- deprecate Python 3.7

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8996d8ad132e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.