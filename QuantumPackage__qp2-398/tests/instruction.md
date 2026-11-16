# Issue

**Title:** cGTOs: complex Boys function, gamma-free series and stable recursions

## Description

For |T| < 3.5, F_n is computed from the series
e^{-T} sum_k (2T)^k / ((2n+1)...(2n+2k+1)) at n_max followed by downward recursion (no gamma() calls; the truncated Taylor polynomials are removed). For |T| >= 3.5, the erf + upward recursion is used only for n <= |T|, where it is stable; higher orders use the series at n_max and downward recursion.

Max relative error on a 16261-point grid, n <= 14 (mpmath reference): |T| < 0.35: 1.7e-13 -> 6.4e-16; 0.35 <= |T| < 3.5: 3.2e-15 -> 2.3e-15; |T| >= 3.5, Re T < 0: 3.2e-12 -> 2.5e-13; Re T >= 0: 2.2e-11 -> 1.6e-14. crint_1_vec is 40-100x faster for 0.35 <= |T| < 3.5.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `009f206eed6b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.