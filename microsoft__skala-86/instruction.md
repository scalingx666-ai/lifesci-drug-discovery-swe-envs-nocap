# Issue

**Title:** Pin pre-commit hook revision to commit SHA

## Description

Replaces the ruff-pre-commit version tag in .pre-commit-config.yaml with the corresponding commit SHA, keeping the version as a # frozen: comment. No version change; the SHA is the commit v0.15.10 resolves to.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6304869125e4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.