# Issue

**Title:** Similarity search with fingerprint rather than SMILES as query

## Description

Hi! I've created a pull request that addresses issue #73. Querying with fingerprints is particularly useful for retrieving molecules by fingerprints predicted from mass spectra using machine learning methods. This approach typically involves querying large databases like PubChem, perfectly fitting the purpose of the FPSim2 package.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `29480193cbe7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.