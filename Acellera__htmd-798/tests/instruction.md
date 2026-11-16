# Issue

**Title:** Remove inverse dihedral types in parameterize

## Description

They were causing issues when zeroing parameters for optimization and are totally unnecessary.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `07533e780346`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.