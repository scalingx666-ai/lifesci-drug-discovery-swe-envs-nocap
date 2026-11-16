# Issue

**Title:** Shuffle llama3 dataset after tokenization

## Description

We want to make sure that we shuffle the dataset after we apply the tokenization so that inputs from the same sequence are shuffled throughout the shuffle buffer

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f01a9d2ea371`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.