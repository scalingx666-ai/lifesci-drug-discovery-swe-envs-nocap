# Issue

**Title:** Compile Cairo from scratch for all Linux builds

## Description

The RDKit draw module raises a segmentation fault if compiled with the cairo version in the CentOS repository. Compiling Cairo from scratch solves this problem.  and #32.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0528d4ad28f1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.