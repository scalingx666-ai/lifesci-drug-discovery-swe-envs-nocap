# Issue

**Title:** Error trap for UHF/UDFT calculations with basis sets containing F functions and CUDA version

## Description

The error trap implemented here should resolve #330.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2a0d1e193538`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.