# Issue

**Title:** Multi arch test

## Description

Add CI for additional CPU architectures, as emulated by QEMU

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d2da45251559`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.