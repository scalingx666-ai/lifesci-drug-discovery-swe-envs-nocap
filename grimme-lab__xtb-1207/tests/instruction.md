# Issue

**Title:** Add initial support of LLVMFlang

## Description

This patch adds support of LLVMFlang (tested with flang-trunk). With some extra patches of 3rd-party deps, all tests are passing without OpenMP. OpenMP builds are not tested yet.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0da232747c17`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.