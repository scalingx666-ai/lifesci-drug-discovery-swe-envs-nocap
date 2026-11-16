# Issue

**Title:** Make sure gpu4pyscf allocator is never used

## Description

There was a theoretical way the gpu4pyscf allocator could escape by someone directly importing backend. 

This does not work now, as backend sets the torch allocator and as a skala package it is imported after the gpu4pyscf everywhere, so only the torch allocator will be used. Tiny fix on #98

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `89878b291bb2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.