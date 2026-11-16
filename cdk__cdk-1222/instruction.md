# Issue

**Title:** Improved stereochemistry invalidation when modifying molecules (Fixes…

## Description

… #1221).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a718006b232c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.