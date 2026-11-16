# Issue

**Title:** Upate compiler versions in CI

## Description

Latest compilers are gcc 11 and clang 13, GCC 5 is no longer supported on macOS so let's try with gcc-7 as an oldest version

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `069382c27597`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.