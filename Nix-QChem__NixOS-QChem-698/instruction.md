# Issue

**Title:** ambertools: 24 -> 25

## Description

Updates to the latest AmberTools version. It tries to apply auto updates when running CMake, which can luckily be disabled.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `12b2053c528a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.