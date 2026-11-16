# Issue

**Title:** Refactor `generate_real_spherical_harmonics_scipy` to use scipy's `sph_harm_y_all`

## Description

The new version of the function is more stable for high `l` values.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0b68e7c367c4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.