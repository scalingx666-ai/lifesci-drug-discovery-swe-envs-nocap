# Issue

**Title:** py3.12 incompatibility with scipy and rdkit update

## Description

**Description**
- [x] rdkit removed from the test extra in the `pyproject.toml` and added as fixture in the `test_run.py`, to be installed by Ersilia  when necessary.
- [x] scipy version version specified in  `pyproject.toml` `version = "<=1.10.0"` is not supported by  `py3.12` and updated to be version = "*` to be compatible withit.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4f099d5a31f0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.