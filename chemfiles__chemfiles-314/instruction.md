# Issue

**Title:** Speed up atom removal in large structures

## Description

Instead of checking each residue to find if the removed atom was inside, directly remove the atom from the corresponding residue

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `da4c316f6e49`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.