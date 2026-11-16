# Issue

**Title:** Avoid some heavy instructions in xtb/hamiltonian

## Description

This patch slightly speeds up evaluation of `build_SDQH0`, `build_dSDQH0`, `build_dSDQH0_noreset` routines by avoiding pow calls in `shellPoly` and `dshellPoly` routines with GCC (Intel compilers use constant propagation here) and sometimes useless divisions in `intgrad.f90`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c769116ca4b5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.