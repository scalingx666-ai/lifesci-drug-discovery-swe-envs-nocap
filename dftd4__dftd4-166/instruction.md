# Issue

**Title:** ILP64 support

## Description

Adds support for BLAS/LAPACK ILP64.

`cmake`:  `-DWITH_ILP64` **and** `DBLAS_LIBRARIES` 
`meson`: `Dilp64=true`

Note that `multicharge` must also have `ILP64` support (grimme-lab/multicharge#16)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3e4ea97f90b2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.