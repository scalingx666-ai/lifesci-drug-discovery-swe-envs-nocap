# Issue

**Title:** Smallmol get bonds warning

## Description

Modified two methods.

1) getBonds that will not crush if no bonds exists in the molecule (eg single atom molecule)
2) toMolecule will raise an error if no atoms coordinates exist

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `abf234355489`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.