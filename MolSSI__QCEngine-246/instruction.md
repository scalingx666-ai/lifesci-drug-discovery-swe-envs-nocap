# Issue

**Title:** fix CI

## Description

<!-- Thank you for your contribution! -->

## Description
CI psi4dev and ani channels were broken b/c
* importing psi4 before installing qcng, and psi4 needs qcng
* DDD branch merge needed pushing to later commit to avoid running test
* the torchani harness broke with the 2.0 release #247, so restricted to <2.0

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [ ] Code base linted
- [x] Ready to go **SQUASH**

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cfcaafdf6ef4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.