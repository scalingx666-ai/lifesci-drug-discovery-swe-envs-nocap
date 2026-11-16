# Issue

**Title:** Update Pydantic

## Description

- update pydantic to version 2.x (via bump-pydantic)
- fix missing type annotated (caused failing tests in tox, which collects the latest version of pydantic)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0dfbd015a3d0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.