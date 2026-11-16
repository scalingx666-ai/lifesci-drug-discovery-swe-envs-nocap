# Issue

**Title:** 163 add pre commit hook with stricter linting

## Description

- [x] Add a strict pre-commit hook to slowly increase code quality.
  - [x] Configured via separate config
    - ruff.toml
- [x] Make ruff non-optional
  - Relax config in pyproject.toml to match current code standard.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `75e6dea45864`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.