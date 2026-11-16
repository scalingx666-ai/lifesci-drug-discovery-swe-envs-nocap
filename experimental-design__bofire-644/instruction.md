# Issue

**Title:** Feature/ Exclude constraints usable in GA

## Description

This PR makes the `CategoricalExcludeConstraint` available for solving with GA in mixed domains:

The constraint is evaluated in the objective function, using the `__call__` method. No gradients are required. 

The fix for #643 is included in this PR

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5126e098ebc4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.