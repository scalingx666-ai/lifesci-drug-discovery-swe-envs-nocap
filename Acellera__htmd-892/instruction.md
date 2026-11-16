# Issue

**Title:** Capture stderr messages in case of RDKit failures

## Description

- [x] Implement `_convertMoleculeToRDKitMol`
- [x] Capture RDKit failures in `detectChiralCenters`
- [x] Capture RDKit failures in `fitGasteigerCharges`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `747e55f3e680`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.