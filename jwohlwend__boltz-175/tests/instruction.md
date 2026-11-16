# Issue

**Title:** Latkins/faster construct paired msa

## Description

Use numba to speed up dataloading. On my machine, iterating over the train dataloader with 0 workers:

Original: 50it [01:42,  2.05s/it]

This: 50it [00:43,  1.14it/s]

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ff18f26edb9f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.