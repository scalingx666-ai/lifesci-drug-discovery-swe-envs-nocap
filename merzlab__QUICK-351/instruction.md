# Issue

**Title:** Disable support for HIP and MPI+HIP builds

## Description

Temporarily disable support for HIP and MPI+HIP builds.  This will be revisited post next Amber release when the CUDA code stabilizes and can be ported to the HIP code.

Related: #344

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ef4d027cad3f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.