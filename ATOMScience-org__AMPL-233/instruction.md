# Issue

**Title:** Feature production

## Description

Trains a model in production mode. This uses the entire dataset in training, validation, and test. If using epochs, it will train exactly max_epochs and save the last one.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `61a275f5e24b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.