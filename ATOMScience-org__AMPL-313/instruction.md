# Issue

**Title:** fix make_weights to correctly change strings to nans while keeping cl…

## Description

…assification nans changing to zeros 

I updated the make_weights function. Previously, only if `is_class = True` were the empty strings turned to nan's. Now, they are turned to nan's no matter what. If `is_class=True` then the nans are subsequently turned to zeros. The test_make_weights.py now passes.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `430ddf1c52e1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.