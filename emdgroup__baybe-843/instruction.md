# Issue

**Title:** Fix mypy error in ContinuousCardinalityConstraint

## Description

Fixes a type error that surfaced because numpy tightened its bundled stubs for `np.sum`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f7fb066bd212`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.