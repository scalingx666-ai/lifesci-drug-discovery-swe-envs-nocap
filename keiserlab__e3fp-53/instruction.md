# Issue

**Title:** Replace required Cython dependency with optional Numba

## Description

Having Cython as a required dependency puts constraints on this package. For example, we have to build wheels for multiple systems. We're only using it to accelerate a single function, so this PR replaces instead uses Numba if available.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eac3c8046e54`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.