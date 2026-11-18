# Issue

**Title:** Fix test script for CUDA and F functions

## Description

Small fix to runtest. Cuda test execution was aborting instead of skipping the tests with F functions when the code is compiled with -DENABLEF=FALSE. Now this is fixed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6369ecd5a728`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.