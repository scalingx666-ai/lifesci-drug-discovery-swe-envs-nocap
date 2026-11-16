# Issue

**Title:** Parse SMILES strings

## Description

Really cool project and very helpful. This PR adds SMILES string support using RDKit. 

For example, styrene
```bash
asciimol C=Cc1ccccc1
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1c8570215bcb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.