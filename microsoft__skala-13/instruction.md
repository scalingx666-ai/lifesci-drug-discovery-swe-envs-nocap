# Issue

**Title:** Update GauXC version

## Description

- include header guards for MPI and CUDA
- download json dependency if not available on system

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `da325654d572`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.