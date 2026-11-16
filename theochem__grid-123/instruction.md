# Issue

**Title:** Add global cache_dict to store loaded npz file #67

## Description

1. Add cache to lebedev grid incase repetitive I/O
2. Add cache contents test
3. Remove redundant cache in atomic level

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6acdeb2fcc7d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.