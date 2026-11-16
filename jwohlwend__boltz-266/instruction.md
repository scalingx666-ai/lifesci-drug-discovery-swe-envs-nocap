# Issue

**Title:** Relax NumPy requirement

## Description

I encountered a dependency conflict installing `boltz` due to the current hard-pin on NumPy to `numpy==1.26.3`. This PR relaxes the requirement to `numpy>=1.26,<2.0`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a9b3abc2c1f9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.