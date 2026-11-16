# Issue

**Title:** Make BoFire compatible to BoTorch 0.13.0

## Description

This PR makes BoFire compatible to the most recent BoTorch release. We should also file a new release in the near future. But, before, I want to have the PR on the randomization in fractional factorials in (@dlinzner-bcs) and maybe also need to have a look at the DoEStrategy.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e4f54db79993`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.