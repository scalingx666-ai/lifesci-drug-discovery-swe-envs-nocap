# Issue

**Title:** Use pre-commit to guarantee good code formatting.

## Description

Add pre-commit to address yapf and flake8. Essentially, this will prevent you from committing code with formatting errors. Feel free to give it a try before merging.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fc8526802d4a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.