# Issue

**Title:** Catch unsupported elements

## Description

- exit if elements between 87 (Fr) and 111 (Rg) are in the structure
- catch unsupported reference charge option instead of implicitly using EEQ charges

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ee8b54f1195e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.