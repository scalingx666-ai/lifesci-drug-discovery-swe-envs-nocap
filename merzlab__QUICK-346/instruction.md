# Issue

**Title:** Support for legacy atomics in cuda f gradient kernels

## Description

In this PR, I have made changes to CUDA F gradient kernels to support legacy atomic add. Users won't be able to run F kernels on Kepler cards though. This is because we moved device pointers and some constants from constant memory into the shared memory. This improves the performance and the implementation we have in F gradient source files ( https://github.com/merzlab/QUICK/blob/326-support-for-legacy-atomics-in-cuda-f-gradient-kernels/src/cuda/gpu_get2e_grad_ffff.cu#L259-L505, https://github.com/merzlab/QUICK/blob/326-support-for-legacy-atomics-in-cuda-f-gradient-kernels/src/cuda/gpu_get2e_grad_ffff.cuh#L1695-L1730) is my experimental implementation. We should implement some templates, clean this up, and update other OEI/ERI/LRI kernels to use shared memory. Will be very useful for performance gain on AMD cards. 
I have also reimplemented the ERI sorting algorithm: https://github.com/merzlab/QUICK/blob/326-support-for-legacy-atomics-in-cuda-f-gradient-kernels/src/cuda/gpu_get2e_grad_ffff.cu#L167-L251. The old sorting algorithm (https://github.com/merzlab/QUICK/blob/326-support-for-legacy-atomics-in-cuda-f-gradient-kernels/src/cuda/gpu.cu#L612-L1137) has a bug and fails for sort high angular momentum ERIs properly. We should move the sorting algorithm I implemented in gpu_get2e_grad_ffff.cu into gpu.cu and do the sorting before the SCF.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f5a80bd4e2a3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.