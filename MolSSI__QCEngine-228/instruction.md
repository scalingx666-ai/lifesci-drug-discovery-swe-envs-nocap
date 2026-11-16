# Issue

**Title:** RDKit MMFF94 and CI

## Description

<!-- Thank you for your contribution! -->

## Description
Adds MMFF94 to RDKit, adds tests for other OpenMM FF's, and re-enables TorchANI CI testing.

WARNING! I had implemented #192 backwards in the method/basis combination, this is also fixed here.

## Changelog description
Adds MMFF94 to RDKit computational abilities.

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `84a524cabd53`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.