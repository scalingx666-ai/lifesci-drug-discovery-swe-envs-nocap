# Issue

**Title:** T07: Fix fingerprint generator error

## Description

## Description
Fixed fingerprint generator function to give a vector as an output #360 
convert `fpg.GetCountFingerprint(mol)` to  `fpg.GetFingerprint(mol)` in `smiles_to_fp` function

## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `50233dbf0797`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.