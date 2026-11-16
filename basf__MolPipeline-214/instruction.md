# Issue

**Title:** Add fix to load molpipeline 0.11 chemprop models

## Description

Adding the state_dict_ref to the parameters of init is not compatible with Molpipeline ChempropModels from 0.11.
This PR modifies the `__setstate__` function to ensure that old moldels still can be loaded.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a6fbb15bfbc7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.