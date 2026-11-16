# Issue

**Title:** Update gauss_Chebyshev pts decreasing order bug

## Description

1. Change gauss_chebyshev to generate increasing order pts.
2. Update docstring misinformation
3. Add notes/comments for this change
Extra: remove cov_radii.npz, no need any more
Credit: Thomas for finding this bug

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d1320f454bbf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.