# Issue

**Title:** Write 3D dimension code in molfile header when writing 3D coordinates

## Description

The SDF writer always wrote the file header as 2D even when the output had 3D coordinates.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0b07865b5337`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.