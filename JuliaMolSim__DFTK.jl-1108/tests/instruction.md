# Issue

**Title:** Add symmetry checks for CPU performance

## Description

This PR adds back some checks on symmetries in the `accumulate_over_symmetries!` function that vanished with #1097. This is important for CPU performance.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fa7ae038d579`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.