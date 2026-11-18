# Issue

**Title:** AWG - fix changes introduced in commit 22349aa14

## Description

Commit 22349aa14
- changed default SCF convergence to 1e-4
- comments in README.md
- configure support for CUDA 11.3

These changes were mistakes. Undo here.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ebea6c48ba87`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.