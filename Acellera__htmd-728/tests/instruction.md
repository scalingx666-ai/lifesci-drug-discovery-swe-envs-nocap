# Issue

**Title:** Minor improvement on voxeldescriptors

## Description

Added option of passing a device array to voxeldescriptors to avoid memory reallocation. Speeds up many of our applications by a decent factor is used correctly.

@j3mdamas I really don't know who else to assign here although I doubt you have any expertise on this.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8e30ddd04a66`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.