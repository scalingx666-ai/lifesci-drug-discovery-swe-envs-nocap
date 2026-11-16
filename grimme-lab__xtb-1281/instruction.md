# Issue

**Title:** Avoid spread intrinsic

## Description

With gfortran, spread intrinsic is not optimized (more precisely this is libgfortran call) and therefore it significantly affects on performance, especially for 3-body terms. 

This patch speeds up gradient code in 1.5-2x times with gfortran as well other parts which I did not measure. By some reason, it also affects ifx but it gives only 10% speed up for `deriv_atm_triple` subroutine. 

I have used unrolled cycles since they provide an extra optimizations for ifx: time was improved from 680 to 625 ms for my input. Usual cycles does not give this improvement: see the assembler difference here: https://godbolt.org/z/zs6e7vzT4. The first source code is the original, the second is presented in this PR and the third one uses cycles. 

I did not touched initializations/io parts where spread are used.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `293469d41e8d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.