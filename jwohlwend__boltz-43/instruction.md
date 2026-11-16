# Issue

**Title:** Added chunking for larger crops inference

## Description

I added chunking to:
1. PairFormer's triangular attention
2. MSAModule's transition layers
3. MSAModule's pair weighted average
4. MSAModule's outer product mean

The chunking gets automatically enabled when crop size is > 1024.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e43f9101886e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.