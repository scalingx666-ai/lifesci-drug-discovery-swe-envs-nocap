# Issue

**Title:** Fixes bug in initialisation of ADC guess vectors

## Description

## Description
When initialising the guess vectors for ADC, an identity matrix in the full space was briefly initialised, which is O(N^6) and O(N^8) in memory for IP/EA- and EE-ADC(2), respectively (!). This oversight is fine for these small examples but is very bad if people wanted to use the code as a reference for larger systems!

## What are your new additions? Please provide a brief list.

* **Changes**
  - [x] Only initialises the required space for the guess vectors.
  - [x] Correctly rotates final eigenvectors on convergence.

## Status
- [x] Click when ready for review-and-merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c15e4d742df4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.