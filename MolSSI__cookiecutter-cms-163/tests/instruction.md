# Issue

**Title:** Update setup.cfg

## Description

Remove metadata and setuptools configuration that is now duplicated in pyproject.toml

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4d453de67c6e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.