# Issue

**Title:** Fix for parameterize RTF writer

## Description

fixes problems with atom types overflowing in the rtf writer causing pr…oblems in psfgen

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `28cd9d4ccd13`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.