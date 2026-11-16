# Issue

**Title:** Fix the expected mask shape for AtomAttentionPairBias

## Description

- The pairwise mask tensor should have the expected shape: (B, N)
- With mask[:, None, None], the matrix will be broadcasted from (B, 1, 1, N) to (B, H, N, N) where H = num_heads, and N = num_tokens

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5f515995cfca`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.