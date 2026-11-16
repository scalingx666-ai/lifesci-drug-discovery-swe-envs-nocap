# Issue

**Title:** Force probabilities to be between 0 and 1

## Description

The probabilities might fall outside that range due to floating point precision, which would cause an error.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5e04f6ce7c3f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.