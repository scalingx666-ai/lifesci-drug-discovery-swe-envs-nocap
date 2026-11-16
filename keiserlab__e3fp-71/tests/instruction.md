# Issue

**Title:** Ensure all array metrics return an ndarray

## Description

This PR  by ensuring that all array metrics return an `ndarray` (previouslty `soergel` returned a matrix).

It also improves and simplifies the array metric test suite and adds docstring testing to CI.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ce3d8c5a0a96`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.