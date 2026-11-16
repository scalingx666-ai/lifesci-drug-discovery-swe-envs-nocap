# Issue

**Title:** Fix serial compilation

## Description

This PR  and #9
- [x] Fixes a bug in ScaLAPACK detection in a serial compilation
- [x] Fixes an inconsistency in the use of HDF5 and UUID when using `cmakeconfig.py` _vs_ bare CMake.
- [x] Adds a couple of serial builds on Linux, so that we catch breaking changes like the ScaLAPACK one.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ea2d6bbaa910`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.