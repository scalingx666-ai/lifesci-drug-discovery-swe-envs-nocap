# Issue

**Title:** fix zero division in configuration recovery

## Description

.

Division by zero was possible if no bits had any probability of being flipped.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ee02f56416bb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.