# Issue

**Title:** GPU| reduce bubbles and kernel overhead

## Description

This PR introduces 2 minor changes when looping over columns of wave functions:

1) There is no need for device synchronization in the loop over the bands of $\Psi$. Each band is treated independently, and there is no risk of race condition. All it does is create bubbles in the GPU execution.

2) Applying `H.fourier_op.multiplier` band by band is not the most efficient on the GPU. There is overhead in launching many small kernels instead of a large one. Moreover, GPU parallelism is better exploited with large arrays.

I did not spot any performance impact on the CPU side. On NVIDIA GPUs, I observe a general speedup of ~10% on the SCF.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c532f4091ab4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.