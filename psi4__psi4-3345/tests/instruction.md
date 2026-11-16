# Issue

**Title:** Try updated Windows constraints for MKL (2025) and OpenMP

## Description

Updated Windows constraints for MKL and OpenMP.

## Description
<!-- Provide a brief description of the PR's purpose here. -->
Give MKL 2025 a try. 🤞 all the Windows trouble with 2024.2 is healed in '25.
On Windows were were hitting limits and stuck at
- [x] MKL <=2024.1, `intel-openmp` (iomp5), and clang 17.0.6 --- wrong answers and dysev errors with newer MKL and omp errors with clang 18 & 19
thanks to a kindly maintainer at c-f determined to get mkl 2025 working (PR linked below) which also switches to `llvm-openmp`, psi4 can now use roughly current packages on windows
- [x] MKL 2025, `llvm-openmp`, clang v19

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3e8888960d94`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.