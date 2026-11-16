# Issue

**Title:** Disable AMDGPU precompilation if !functional

## Description

Hopefully this will fix the DFTKAMDGPUExt precompilation errors on CI, which seem to become fatal in Julia 1.12. (But are generally annoying in 1.10 already...)

@abussy looks good right?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c9b9149ff778`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.