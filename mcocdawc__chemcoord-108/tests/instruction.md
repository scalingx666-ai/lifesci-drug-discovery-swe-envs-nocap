# Issue

**Title:** enforce more checks

## Description

- actually enforce `ruff check`
- actually enforce `mypy`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a35c2a70b674`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.