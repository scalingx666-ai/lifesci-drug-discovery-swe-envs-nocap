# Issue

**Title:** Fix GitHub workflow GNU builds

## Description

BLAS is now detected from libopenblas, so the build will succeed

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1a383501a9a0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.