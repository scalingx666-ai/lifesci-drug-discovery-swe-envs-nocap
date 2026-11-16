# Issue

**Title:** ConjugatedPiSystemsDetector allene handling fix

## Description

Fixes issue with path-dependent conjugated system detection if allenes are involved, especially if the allene is the first atom.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `73b28be5705a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.