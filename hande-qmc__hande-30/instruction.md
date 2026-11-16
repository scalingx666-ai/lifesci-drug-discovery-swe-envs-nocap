# Issue

**Title:** In Weighted Sampling, Place Hamiltonian Transformation into Null Excitation Test

## Description

Addressing #29 , this fix puts Hamiltonian transformation into null excitation test, ensuring that the connection is valid before `trial_fn` attempts to create a new determinant according to `connection`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9f56fb086958`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.