# Issue

**Title:** fix small issues in SBDD dataset support

## Description

1. update biopandas installation warning, processing message, warning for long time processing
2. save atomic number instead of one-hot encoding
3. add protein remove Hs and ligand remove Hs as two different options
4. fix error about mismatch between protein atom coordinate and atom type
5. update google doc accordingly
6. move failure reporting to the end

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `af88629556c4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.