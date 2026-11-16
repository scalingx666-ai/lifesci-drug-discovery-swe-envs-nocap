# Issue

**Title:** Analytical gradient for coordination number (CN)

## Description

- [x] implementation
- [x] testing (against `s-dftd3` and numerical)
- [x] batched 

Note: In `s-dftd3` and the numerical solution, the same atom is not masked as in the PyTorch implementation.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `09ec34f881a6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.