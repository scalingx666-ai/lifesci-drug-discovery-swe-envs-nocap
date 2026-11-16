# Issue

**Title:** 3.0.2 maintenance

## Description

- Avoid using meson 1.8.0 in CI (adapted from )
- Update tblite submodule
- Avoid algorithm termination after unsuccessful crossing

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `19d98ba4e63f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.