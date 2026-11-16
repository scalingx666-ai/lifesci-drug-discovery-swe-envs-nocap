# Issue

**Title:** GP Cleanup

## Description

* Cleans up the `GaussianProcessSurrogate` class
* Adds transfer learning tests asserting that the mechanism works regardless of which tasks are represented in the training data

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2c5552dcba30`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.