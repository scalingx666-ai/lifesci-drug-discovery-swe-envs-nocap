# Issue

**Title:** Port stress/response calculations to the GPU

## Description

This PR enables ForwardDiff calculations (stress and response) on the GPU. Main changes are:

1) Data transfer from/to the device where necessary
2) Various small changes to avoid GPU compiler confusion (e.g. see changes in `src/workarounds/forwarddiff_rules.jl`)
3) CPU fall-backs for all XC operations taking place in the `DftFunctionals.jl` package
4) Refactoring of the ForwardDiff tests, such that all tests can be run on various architectures (CPU, CUDA, AMDGPU)

With this PR, all ForwardDiff workflows currently tested on the CPU successfully run on both NVIDIA and AMD GPUs.

Future improvements will come with:
- PR #1185 for the tests to consistently finish on GPUs (right now, they regularly fail due to Cholesky instability on the GPU)
- PR  to pave the way for XC operations on the GPU
- PR #1163 for more efficient `PlaneWaveBasis` instantiation

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `74b728a17b4a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.