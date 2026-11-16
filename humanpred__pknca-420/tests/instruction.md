# Issue

**Title:** Feat request: Add lambda.z.time.last in half.life calculation

## Description

This PR introduces a new feature to the `pk.calc.half.life` ffor the calculation of `lambda.z.time.last`, which represents the last time point used for terminal slope estimation. The changes affect the function's file (half.life.R), documentation, and all related results tests.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `73b181e54b4b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.