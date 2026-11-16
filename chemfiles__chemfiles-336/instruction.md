# Issue

**Title:** Fix Frame::out_of_plane for co-linear atoms

## Description

The code would return NaN if atoms `i, k, m` were colinear. I think 0 is a much more reasonable value here

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `99486730d484`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.