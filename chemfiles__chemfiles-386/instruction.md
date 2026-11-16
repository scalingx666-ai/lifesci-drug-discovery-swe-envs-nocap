# Issue

**Title:** fix: reject rotated orthorhombic cell matrices

## Description

by rejecting unit cells that are not diagonal and orthorhombic. This means orthorhombic UnitCells can be constructed from diagonal matrices only.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `594f265f3f11`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.