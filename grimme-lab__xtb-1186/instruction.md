# Issue

**Title:** Avoid integer overflow in main/geometry.f90

## Description

Integer `(kind=4)` overflow may be easily achieved at line:
https://github.com/grimme-lab/xtb/blob/7b9935b95138893db86045ac74864883b3424e9b/src/main/geometry.f90#L153

To avoid this,  variables `maxdist`, `maxbend`, and `maxtrsn` have integer `(kind=8)` type now.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7b9935b95138`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.