# Issue

**Title:** Add workflow for building wheels

## Description

Allows to build manylinux wheels for the Python bindings. Somewhat suboptimal since we have to redistribute OpenBLAS here, which makes the package huge (compared to a binary statically linked against MKL).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f572723f5a5c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.