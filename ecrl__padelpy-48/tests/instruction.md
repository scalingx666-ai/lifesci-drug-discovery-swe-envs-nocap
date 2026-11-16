# Issue

**Title:** Update install method, update unit tests

## Description

No functional changes, but:

- Build/installation now uses `pyproject.toml` instead of the deprecated `setup.py`
- Removed Azure-based unit testing, using GitHub workflows and `pytest`
- New releases are automatically deployed to PyPI

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `05f08da901d0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.