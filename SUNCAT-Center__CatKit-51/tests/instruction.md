# Issue

**Title:** Split only after the first underscore ('_') in structure folder name …

## Description

…and preserve the rest.

This is useful the structure name itself is more complex (e.g. `A_a_225` instead of `fcc`).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3d6ff1520d07`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.