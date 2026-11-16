# Issue

**Title:** Treat Intel LLVM compiler as standard Intel compiler

## Description

These changes ensure that the Intel LLVM compiler is treated as the standard Intel compiler, addressing specific compatibility issues we've encountered.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4aa9e7909ccc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.