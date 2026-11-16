# Issue

**Title:** Generalize dropping leaving atoms for covalent modifications and noncanonical modifications.

## Description

Some modified residues (CCD Code 4OO for example) don't have the OXT atom labelled appropriately but do have it marked as a leaving atom. This pull request standardizes the behavior of dropping leaving atoms in residue modifications.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9ab9d62cf6ac`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.