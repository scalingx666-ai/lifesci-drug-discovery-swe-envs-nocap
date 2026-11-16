# Issue

**Title:** Make final GFN2 optimizations in QCG optional

## Description

For QCG, no GFN2-xTB optimization after each step will be performed if GFN1-xTB or GFN-FF is selected except for when the `-fin_opt_gfn2`keyword is given.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8da0aeeb3068`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.