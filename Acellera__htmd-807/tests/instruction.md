# Issue

**Title:** Scipy minimizer

## Description

Changed minimizer to scipy.
Added tests for glycol since h2o2 doesn't have any atoms to minimize on the dihedral scans.
Reinitiate the MM minimizer with the better charges after the charge guessing.

Data PR:

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eb65777b3a60`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.