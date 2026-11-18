# Issue

**Title:** Vector bugfix

## Description

This fixes a bug for still images of pbc systems with both axes and custom vectors requested where neither or only one was shown.

I made additional changes to treat these two vector sources the same by combining the sources of vectors early, so a consistent set of transformations can be applied without duplicating work.

I also unified the scattered means by which rotation is applied so it is the same scheme for vectors, the lattice box and all tests.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ec0db54fa813`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.