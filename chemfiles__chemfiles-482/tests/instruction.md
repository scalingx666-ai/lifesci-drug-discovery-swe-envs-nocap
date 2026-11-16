# Issue

**Title:** Faster XTC decoding

## Description

This PR adds faster decoding of integers which are stored as <= 64 bits. For these values, integer arithmetic can be used as proposed [here](https://doi.org/10.1186/s13104-021-05536-5) and implemented by [libxtc](https://gitlab.com/impulse_md/libxtc).

libxtc also has a special implementation for larger ints using 128 bit ints. I found that these lengths are rather unusual in "typical" MD trajectories.
Instead, the old algorithm is used to decode those values here eliminating special compile time checks for the presence of 128 bit types.

Also, a testcase for these large ints is added to test the old code paths.

The changes reduce the time to read the `ubuquitin.xtc` test file by more than 20%.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0b5f9da07d41`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.