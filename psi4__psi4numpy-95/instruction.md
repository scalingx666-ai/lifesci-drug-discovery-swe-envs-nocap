# Issue

**Title:** SCF Vibrational Circular Dichroism (VCD) Simulations

## Description

## Description
Adds SCF VCD capabilities to Psi4NumPy

## TODOs
Notable points (developer or user-interest) that this PR has or will accomplish.
  - [x] Reproduce SCF Hessian results using generalized density formalism
  - [x] Reproduce calculation of normal modes
  - [x] Reproduce dipole strengths
  - [x] Calcuate Atomic Polar Tensors (APTs) using dipole derivatives from Psi4
  - [x] Calculate Atomic Axial Tensors (AATs) using half overlap derivatives from Psi4
  - [x] Calculate rotatory strengths

## Any questions for the community?
- [x] None atm

## Status
- [x] Click when ready for review-and-merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4c359bcbf1c1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.