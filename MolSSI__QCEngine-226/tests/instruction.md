# Issue

**Title:** OpenMM Harness Method/Basis overhaul

## Description

<!-- Thank you for your contribution! -->

## Description
Applies method/basis discussion from issue #192 and fixes issues with the value of the energy and the gradient scale.

## Changelog description
Moves the OpenMM harness to a canonical forcefield based method/basis language combination.

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3aa8c6799362`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.