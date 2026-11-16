# Issue

**Title:** pkg_resources related fixes

## Description

- Removed the references of pkg_resources
- Deleted top level of __init__.py
- Updated setup.py

Tests:
- Made sure the ci jobs run fine.
- Created cpu env, build atomsci packages. Ran unit tests and a few integrative tests on LC to verify.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `df6adbcc5440`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.