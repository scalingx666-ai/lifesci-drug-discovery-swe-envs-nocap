# Issue

**Title:** Add Convenience Kernel Arithmetic

## Description

DevPR, parent is #745 

### Features
- Adds `mul`, `rmul`, `add`, `radd` operators for BayBE kernels
- Ensures flattening of add and mul operatrions, eg `SumKernel([SumKernel([a, b]), c])` results in `SumKernel([a,b,c])`
- Multiplication wth a constant will result in a `ScaleKernel` with the new attribute `outputscale_trainable=False` which results in it not being affected by training, ie it is constant

### Postponed
* Rename `AdditiveKernel` to `SumKernel` + deprecation + deserialziation hook for compatibility

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `af70d31be110`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.