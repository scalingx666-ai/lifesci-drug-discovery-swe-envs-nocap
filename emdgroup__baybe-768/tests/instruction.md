# Issue

**Title:** Use `np.isclose` for checking bounds of `Interval`

## Description

This PR changes the way that the bounds of `Interval` objects are compared by using `np.isclose`.

This  as now, the two objects `Interval(0, 0.9999999)` and `Interval(0,1)` are considered equal.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `48f634f1abcd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.