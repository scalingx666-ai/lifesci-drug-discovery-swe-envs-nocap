# Issue

**Title:** Support for latest Python

## Description

- add setuptools as explicit dependency for building extension modules with cffi
- test Python 3.11 to 3.13 in CI

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7b2ff85a71a3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.