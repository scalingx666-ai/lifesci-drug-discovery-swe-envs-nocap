# Issue

**Title:** Fixes for training and Torch compatibility

## Description

Remove unused return value in diffusion.forward() (used during v2 training), convert use_kernels argument to positional only for torch>2.2 compatibility.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `21bcdaf37639`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.