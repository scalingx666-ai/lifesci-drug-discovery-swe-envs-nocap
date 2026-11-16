# Issue

**Title:** Remove molvs dependency

## Description

The SMILES standardization functionality from the molvs package was integrated into RDKit a long time ago, and molvs is no longer maintained. This PR changes the standardization functions in utils/struct_utils.py to use the RDKit functions rather than molvs, and removes molvs from the AMPL virtual environments.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a9946f71df6d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.