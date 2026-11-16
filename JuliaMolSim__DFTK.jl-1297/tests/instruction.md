# Issue

**Title:** Reduce allocations in LOBPCG

## Description

Reducing allocations in LOBPCG by pre-allocating arrays and taking views, rather than reallocating at each iteration.

Performance wise, I observe a speedup of LOBPCG from 0% to 10% depending on system size and architecture. It is never slower.

Less allocations also means less pressure on the GC in general, and a lower risk of memory fragmentation on the GPU (as far as I understand). This is hard to measure though.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b216458179f5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.