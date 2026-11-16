# Issue

**Title:** format code with black + isort update

## Description

Format code base with new versions of black and isort. Currently the actions are failing without this.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8190785d7ec0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.