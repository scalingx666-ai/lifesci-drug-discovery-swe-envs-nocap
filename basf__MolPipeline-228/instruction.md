# Issue

**Title:** Random Forest baseline functions

## Description

Add convenient functions to get better baseline configurations of Random Forest in comparison to sklearn defaults with binary Morgan fingerprints.


Optional features to add/discuss:

- [x] add a flag to the convenient functions to enable automated error handling when reading molecules
- [x] add URL to paper in README when it is online
- [ ] add parameter to calibrate with callable like CalibratedClassifierCV
- [ ] add baseline/convenience functions for chemprop/chemeleon

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a68693480cab`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.