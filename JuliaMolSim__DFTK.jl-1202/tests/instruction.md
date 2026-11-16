# Issue

**Title:** Workaround for AMDGPU 5-argument mul!

## Description

A new AMDGPU bug has arisen:  Using the 5-argument `mul!(C, A, B, α, β)` with ROCArrays is extremely slow when the scalars `α, β` are not of the same type as the array elements. The observed slow down is proportional to array size.

This issue only happens with AMDGPU, and not CUDA.

This PR introduces a workaround to ensure type conversion (promotion) of the scalars when necessary. I tried to fit it in a single function definition, but failed due to infinite recursion issues when the types are not precise enough.

This brings significant speed up for medium to large systems. The LOBPCG of the usual rattled aluminium benchmark is accelerated by ~30% (total calculation accelerated by > 15%). The impact is negligible on SrVO3.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3d74861c3731`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.