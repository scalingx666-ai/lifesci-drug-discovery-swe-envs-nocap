# Issue

**Title:** Avoid large GFN-FF OMP stack allocations

## Description

While looking into  I hit some stack overflows when trying to reproduce. Its been previously documented in  that OMP reductions are the likely cause for this heavy stack usage and  did some work removing unneeded/bloated reductions for GFN2. 

I confirmed that the OMP reductions were the main source of the problem for this case and followed a similar strategy to #1350 to remove them. The `amat` and `dadr` arrays can actually be shared across the threads, as each iteration only needs distinct elements of these arrays. For the roughly ~1900 system from #1382, `dadr` was eating ~80MB per thread and `amat` would use 27MB per thread. Other arrays that still need to be reduced are now stored on heap.

For a 1000 atom benchmark, I didn't see more than 2% difference in runtime before and after this change, which was inline with run-to-run noise anyway.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b31754bf3c7c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.