# Issue

**Title:** Optionally depend on `openbabel`, not separate deprecated wheel

## Description

Open Babel 3.2.0+ now provides pre-built wheels on PyPI.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `15f1d7702e82`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.