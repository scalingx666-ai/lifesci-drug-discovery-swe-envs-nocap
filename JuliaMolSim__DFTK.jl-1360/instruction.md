# Issue

**Title:** Fix GPU in nonlocal term

## Description

#1348 broke the GPU implementation because `D` matrix of the nonlocal term was not copied to the device anymore.

This highlights again the need for a GPU CI, I'll open an issue to discuss this.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8addec44d62c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.