# Issue

**Title:** Enable Python 3.14 host runtime in wheel build workflow

## Description

- [x] Revert setup-python host Python change (back to `3.x`)
- [x] Update cibuildwheel pin to a real existing version that supports Python 3.14 wheels (`3.4.1`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e0b9ad11288d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.