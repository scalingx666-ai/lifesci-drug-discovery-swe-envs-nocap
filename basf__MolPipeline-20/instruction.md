# Issue

**Title:** Fix scorer sign error

## Description

This PR fixes a bug where loss functions were not instantiated correctly when using ignored_value_scorer as the sign was not considered

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e920f4e4238f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.