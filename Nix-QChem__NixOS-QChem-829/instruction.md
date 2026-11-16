# Issue

**Title:** vmd: remove 1.9.3 source-distribution and unconditionally use 2.0.0

## Description

This removes the old source code version of VMD. The new version is currently only available as binary distribution, but although it requires CUDA at build time, it doesn't require CUDA at runtime. This works on my AMD GPU without any issues so far.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e2fd2244f12a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.