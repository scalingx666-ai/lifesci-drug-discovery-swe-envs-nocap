# Issue

**Title:** Fix cuda dependency conflicts

## Description

Somehow  broke main, by making the gpu conda environment not resolvable. 

This fixes it as we do not need the whole cuda toolkit.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `936802b7dc27`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.