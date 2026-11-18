# Issue

**Title:** Fix for issue 337

## Description

The enclosed change should resolve #337. It seems that ifort represent logical true using 255 rather than 1. As a result, when we pass the "is_oshell" flag value from Fortran to C code (https://github.com/merzlab/QUICK/blob/master/src/cuda/gpu.cu#L385-L402), the value in C code was not set properly, and closed shell kernel was invoked for open shell XC calculation (https://github.com/merzlab/QUICK/blob/master/src/cuda/gpu_getxc.cu#L98-L113). Please test and merge.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f5a80bd4e2a3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.