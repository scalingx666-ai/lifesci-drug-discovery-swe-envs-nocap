# Issue

**Title:** Add C Bindings to Atomsk

## Description

We are hoping to make a Julia package that wraps Atomsk. To do this, we need C bindings to be able to call the Atomsk shared object file. This pull request implements C bindings, implements a new Makefile option (`clib`) to include this, and changes the `POLYCRYS` subroutine to retain `P` and `H` when called from Julia.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2b49f877121d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.