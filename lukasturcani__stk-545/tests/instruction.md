# Issue

**Title:** Update parameter from path to database and fix readme bug.

## Description

Missed this one in #544 

Also fixed the README for pypi. Running ``uv run twine check dist/*`` prior to pushing could avoid this

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5c51dd6924bc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.