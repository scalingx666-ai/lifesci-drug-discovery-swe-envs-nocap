# Issue

**Title:** fix fsdp2 checkpoint load

## Description

We need to pass the dataloader even if we're not loading it from a checkpoint, since it gets passed through as none otherwise.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9467487d12de`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.