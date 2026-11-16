# Issue

**Title:** Fix for use_kernels for later torch versions for PairformerNoSeqModule

## Description

Make use_kernels positional arg in PairformerNoSeqModule to avoid torch issues when use_reentrant=False is not passed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8b1627c9dc79`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.