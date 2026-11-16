# Issue

**Title:** Sync dependencies between pyproject.toml and CI image

## Description

Up to now it has been independently installed in the CI images.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `384ff77e0718`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.