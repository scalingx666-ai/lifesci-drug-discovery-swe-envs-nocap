# Issue

**Title:** ASE and RDKit

## Description

Optional dependency on ASE; if existing, support all ASE formats, as well as automatically resolving SMILES by searching PubChem

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9b35438a31ff`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.