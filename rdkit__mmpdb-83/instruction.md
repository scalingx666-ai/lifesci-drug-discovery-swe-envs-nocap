# Issue

**Title:** Fix max_frac_trans option for specific edge cases

## Description

Function get_max_constant_radius_for_fraction_transfer did not correctly return the maximum radius for a constant if min_radius != 0. I adapted these cases to correctly respect min_radius as the lower limit.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `583dc1c0a82f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.