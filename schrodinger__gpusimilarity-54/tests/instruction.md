# Issue

**Title:** Add a recipe to build a docker container

## Description

This will be the preferred way of building/executing GPUSimilarity going forward.  We'll also post public containers at release version so people don't have to worry about building as long as they have nvidia-docker installed.

Further documentation required for all that to be possible.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1570f5c46ff2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.