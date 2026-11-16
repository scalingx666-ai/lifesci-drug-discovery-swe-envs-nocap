# Issue

**Title:** Fix pydantic warnings

## Description

- update remaining old pydantic syntax
- pin pydantic version
- fix tests (tox now runs without errors)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9cbb004549fc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.