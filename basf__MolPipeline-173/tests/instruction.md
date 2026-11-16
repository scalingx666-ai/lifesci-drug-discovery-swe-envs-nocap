# Issue

**Title:** sdf2mol: keep properties from file and add tests

## Description

Properties defined in the SDF were discarded. Now they are kept and stored in the molecule data structures.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6d31e13d52d1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.