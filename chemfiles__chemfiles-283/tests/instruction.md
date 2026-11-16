# Issue

**Title:** Do not resize frames to 0 when reading

## Description

There is no need to resize frames when reading to them, a new frame is created in Trajectory::read anyway.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a5bf698ee937`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.