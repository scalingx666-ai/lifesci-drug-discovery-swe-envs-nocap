# Issue

**Title:** Remove Hermitian norm dispatch

## Description

GPUArrays v11.5.4 introduces a `norm` function for generic `AbstractGPUArrays`, which also works for Hermitian matrices. As a result, the current workaround `norm` becomes ambiguous, and the calculation crashes when it is called.

The simplest fix is to remove the workaround. However, since DFTK does not explicitly depend on GPUArrays (but only GPUArraysCore), we cannot restrict the compatibility in `Project.toml`. I think it is ok, and we can safely assume the latest GPUArrays version is used.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9c9f6f813902`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.