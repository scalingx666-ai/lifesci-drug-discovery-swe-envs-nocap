# Issue

**Title:** moved conf level ad introduced two new nc functions

## Description

1. Added two nc functions, the log and one SVM specific.
2. Removed from the initializer the confidence level as it is needed only on inference and is less confusing to the user.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `625977838090`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.