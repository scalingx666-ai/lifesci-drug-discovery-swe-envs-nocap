# Issue

**Title:** Read correct frame indices from TNG

## Description

Depends on 

Updates the external TNG library to read the correct number of frames in a trajectory. Additionally, store the time of a frame as property, if present.

.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b2ad6c60d0bf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.