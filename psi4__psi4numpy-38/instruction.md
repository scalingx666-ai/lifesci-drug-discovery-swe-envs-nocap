# Issue

**Title:** RHF gradients and hessians

## Description

## Description
This PR implements Nuclear Gradients and Hessians of RHF Wavefunction calculated using derivatives of integrals obtained from psi4. This will work once my pull request regarding exporting these integrals gets merged into PSI4. @kcpearce will soon start coding MP2 Gradients and Hessians in Psi4Numpy on another PR using this machinery. Once that is done, we would like to go for CCSD Hessians.
## What are your new additions? Please provide a brief list.
* **New Features**
  - [X] RHF Nuclear Gradients
  - [X] RHF Nuclear Hessians

## Status
- [x] Click when ready for review-and-merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `aec147587e39`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.