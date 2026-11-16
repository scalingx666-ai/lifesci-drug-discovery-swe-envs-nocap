# Issue

**Title:** Enable gradient computation of SCF gradients

## Description

See https://pytorch.org/docs/stable/generated/torch.cdist.html for details on *compute_mode*.

Also, enables batched SCF.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `51036b09187e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.