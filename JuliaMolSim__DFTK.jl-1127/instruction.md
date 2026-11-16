# Issue

**Title:** Use columnwise_dots where applicable

## Description

PR #1068 introduced generic linear algebra functions and their optimized GPU implementations for LOBPCG. It turns out that they can be used elsewhere in the code. In particular, `columnwise_dots` is relevant for various Hamiltonian terms.

This has some performance impact on GPU runs: evaluation of the kinetic energy becomes negligible, and cost of nonlocal forces is reduced by 25% - 50% (depending on test system). CPU timings are not affected.

I moved the `/eigen/linalg.jl` file to `/common/linalg.jl` since usage goes beyond LOBPCG now.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6cf912e4971b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.