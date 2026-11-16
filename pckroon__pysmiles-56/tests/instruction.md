# Issue

**Title:** Improved bond order assignment

## Description

.

Algorithm now first picks bonds that must always have higher order.

A warning is issued if assignment is incomplete.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5bf87458359a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.