# Issue

**Title:** Calculate gradient before diag in IRC

## Description

Ensures the Lagrange multipliers are properly calculated before
attempting to diagonalize the Hessian of the Lagrangian in the IRC
module.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5f5a47c98c1b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.