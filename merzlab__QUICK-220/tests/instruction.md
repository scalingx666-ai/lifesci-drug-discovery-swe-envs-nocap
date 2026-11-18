# Issue

**Title:** Improvements to OEI kernels

## Description

I have eliminated register spillage of OEI kernels and made some improvements. Please review and merge.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c697e74c80b6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.