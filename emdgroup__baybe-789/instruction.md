# Issue

**Title:** GP Criterion

## Description

DevPR, parent is 

Makes the optimization criterion of the `GaussianProcessSurrogate` model configurable, in the form of a new `FitCriterion` enum. Potentially, this might be generalized to a class-based approach in the future if more configuration options are required, but for now the simpler solution serves all existing use cases.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f1e7a0b9a0a5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.