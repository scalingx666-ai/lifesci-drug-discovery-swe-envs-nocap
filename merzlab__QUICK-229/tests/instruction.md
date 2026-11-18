# Issue

**Title:** Some minor updates to configure build system

## Description

In this PR, I have updated configure script to 1) handle latest CUDA versions, 2) disable compiling f functions in the ERI code by default.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `20b593bc81ef`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.