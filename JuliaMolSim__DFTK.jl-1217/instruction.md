# Issue

**Title:** mGGA optimizations and GPU porting

## Description

I recently realized that mGGA was, in fact, not ported to the GPU. This PR fixes this, and adds a relevant GPU test.

Various optimizations where also done to reduce allocations, and reuse pre-computed data. Most of these optimizations where already mentioned in a TODO. Note that pre-computing `G_plus_k` has the biggest impact, particularly on the GPU.

With these modifications, the cost of applying `divAgrad` is almost exactly 3x that of applying `local` (as good as it gets). Previously, it was about 3.5x on the CPU.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4b1dd1556d1e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.