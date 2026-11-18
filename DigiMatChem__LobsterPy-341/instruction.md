# Issue

**Title:** Ci updates

## Description

# Changes

1. Remove redundant flake8 as we already use ruff
2. Run autoupdate pre-commit hooks

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2f883b246c35`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.