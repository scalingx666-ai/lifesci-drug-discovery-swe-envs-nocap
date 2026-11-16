# Issue

**Title:** Pre opt update

## Description

## Description
This PR allows conformers that fail to be pre-optimised to pass to the next stage by using the last conformer in the trajectory as the starting point for the full `qm_optimise` stage.


## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `41f73af2f0f3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.