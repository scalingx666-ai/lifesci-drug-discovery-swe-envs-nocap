# Issue

**Title:** Fock matrix as convergence property

## Description

- allow different types of self-consistent parameters (scp), i.e., the variable which is convergenced in SCF
- available scps: charge, potential, Fock matrix

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e6392c7bc313`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.