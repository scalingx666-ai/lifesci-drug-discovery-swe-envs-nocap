# Issue

**Title:** Add max_dim argument to diagonalize_fermionic_hamiltonian

## Description

Fixes #

The maximum dimension is given as a pair `(max_dim_a, max_dim_b)` (you can just specify a single integer if you want them to be the same). In each iteration, the bitstrings are picked in this order, until the maximum dimension is reached:
- Explicitly requested bitstrings
- Carryover bitstrings. If there are more carryover bitstrings than we can pick without exceeding the maximum dimension, we pick them randomly (uniformly without replacement).
- Bitstrings sampled from the QPU. If there are more sampled bitstrings than we can pick without exceeding the maximum dimension, we pick them randomly (uniformly without replacement).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `780c30c68c87`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.