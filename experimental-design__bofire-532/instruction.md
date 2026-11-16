# Issue

**Title:** Blocking for Fractional Factorial Designs

## Description

This PR adds blocking for fractional factorial designs, currently it is not supported for fractional factorial designs. But this can be implemented in a straight foward manner. Only thing necessary is to add the blocking generators to `/bofire/bofire/utils/default_fracfac_generators.py` and update the getters. I will take care for this in a seperate PR when this one is merged.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1e62c35b2bcb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.