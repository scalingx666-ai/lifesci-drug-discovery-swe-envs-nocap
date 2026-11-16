# Issue

**Title:** Modernize python packaging

## Description

- Replace setup.py with pyproject.toml
- Remove requirements files
- Remove MANIFEST.in
- Add uv.lock

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `88992651019f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.