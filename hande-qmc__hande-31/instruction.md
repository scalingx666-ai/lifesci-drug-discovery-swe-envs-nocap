# Issue

**Title:** Complex DMQMC Doesn't Support Weighted Sampling.

## Description

Haven't noticed `spawn_weighted_sampling` sets `nspawn_im` to zero. Should add a check for this.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9f56fb086958`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.