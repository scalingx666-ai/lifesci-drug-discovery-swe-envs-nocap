# Issue

**Title:** Compile models and losses with TorchScript for training and inference

## Description

PR #11 did all the refactoring needed to compile the models with TorchScript but did not contain the last commit which implements the actual compilation. This PR pushes the missing commit.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `39985f368677`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.