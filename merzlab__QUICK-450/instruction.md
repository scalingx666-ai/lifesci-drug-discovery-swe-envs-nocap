# Issue

**Title:** Fix GPU architecture selection and print nvcc flags to build report

## Description

Replace MATCHES with STREQUAL.
Otherwise "-DQUICK_USER_ARCH=blackwell2" would trigger blackwell and blackwell2 build.

Also print nvcc flags.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ae832f993969`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.