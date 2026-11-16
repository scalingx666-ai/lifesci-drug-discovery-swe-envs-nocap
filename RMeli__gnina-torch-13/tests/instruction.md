# Issue

**Title:** Move output transforms

## Description

The different `output_transform` functions are moved to a separate module and they are now tested explicitly.

The function setting up all metrics has also been moved to its own module for clarity.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b573ce321f7d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.