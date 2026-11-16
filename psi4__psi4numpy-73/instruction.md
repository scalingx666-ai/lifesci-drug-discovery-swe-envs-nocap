# Issue

**Title:** RHF with symmetry

## Description

## Description

This adds a reference implementation of RHF with integral symmetry, except for the JK build, which is modeled after the Psi4 implementation rather than the Crawford group tutorial.

## What are your new additions? Please provide a brief list.
* **New Features**
  - [x] Reference implementation of RHF with symmetry
  - [x] Added basic transformers to `helper_HF.py`

## Status
- [x] Click when ready for review-and-merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6dc97954ba2f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.