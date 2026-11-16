# Issue

**Title:** Use numpy functions

## Description

There are a few numpy functions such as `numpy.cross` which were not available for numba when I wrote the package.
With this PR the corresponding numpy functions are used instead of the custom ones.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9165c76dc639`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.