# Issue

**Title:** Implement own use_torch_mempool_in_cupy

## Description

Implements 


This allows us to only use the toch allocator globally. We thus do not have to reset allocators or have problems with dlpack as it all stays with the torch allocator.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0a2326ba0aaf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.