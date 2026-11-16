# Issue

**Title:** fix issue with non-linux installation

## Description

Removing the `cuequivariance` requirement from the default installation, to enable installation on non-Linux devices

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8bf88eadf8c8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.