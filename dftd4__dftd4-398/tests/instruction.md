# Issue

**Title:** Analytic second derivatives for ATM

## Description

This PR implements analytic second derivatives for the ATM contribution.

The implementation includes the full coordination-number chain rule and supports D4/D4S, smooth cutoffs, periodic systems, and work partitioning. The analytical ATM Hessian is OpenMP-parallelized, including the three-body evaluation, coordination-number Hessian contraction, and final Hessian assembly; it also supports work partition.

The existing `--hessian` path now evaluates the total Hessian as the sum of the numerical two-body contribution and the analytical ATM contribution.

The analytical result is validated against finite differences of the ATM gradient, including D4/D4S, smooth cutoffs, periodic systems, and partitioned calculations.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c0aaced7c6af`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.