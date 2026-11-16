# Issue

**Title:** Write MOFid and MOFkey

## Description

Updates the MOFid format to list metadata more clearly.  Also implements the MOFkey format based on the InChIKey and saves these values when analyzing a folder of CIFs in bulk.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f8e6f36f18e2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.