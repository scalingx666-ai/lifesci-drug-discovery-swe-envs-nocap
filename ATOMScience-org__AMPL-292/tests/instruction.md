# Issue

**Title:** Akp moe

## Description

I updated the `scale_moe_descriptors()` function to get rid of fragmented DF warnings from Pandas. Instead of inserting the column in situ, I create a list of columns (`pd.Series` objects) and concatenate them with `pd.concat()` - please check my logic, though.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e3e9b6968c7a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.