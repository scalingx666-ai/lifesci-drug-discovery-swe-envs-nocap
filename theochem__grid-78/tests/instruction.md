# Issue

**Title:** Add a new becke weight function

## Description

1. Separate q P_A calculation from becke weights
    evaluation
2. Add a new compute_weight outer loop for compute
    becke weights for each section of points

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d35d409e3f4d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.