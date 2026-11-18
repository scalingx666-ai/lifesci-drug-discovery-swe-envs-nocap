# Issue

**Title:** Fix atomic descp

## Description

1. Atomic descriptor generation fix: Ensures consistent atom ordering by preserving explicit hydrogens during SMILES parsing (removeHs=False), preventing index mismatches in atomic descriptors.

3. Atomic mapping name fix: Updates atom match naming to include the atom symbol for single-atom patterns.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `235b6709b802`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.