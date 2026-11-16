# Issue

**Title:** Adds ADC(2) reference implementations

## Description

## Description
This PR adds reference implementations for the ADC(2) method, with a separate implementation for ionization potentials, electron affinities and excitation energies. The implementations are based on an RHF reference, but use spin-orbitals as the equations are nicer there. There is also a helper script with a function to perform the Davidson algorithm for an arbitrary matrix, or function defining a matrix-vector product. The latter is adapted from the EOM-CCSD implementation. These are not particularly efficient, but should be a simple enough showcase of the iterative eigensolver to keep the scaling down.

I have tested these scripts against PySCF for the IP and EA, and against adcc for the EE. The codes will not account for degeneracy in `n_states` nor separate singlets and triplet EEs as adcc does, but the energies themselves match.

## What are your new additions? Please provide a brief list.
* **New Features**
  - [x] ADC(2) for ionization potentials
  - [x] ADC(2) for electron affinities
  - [x] ADC(2) for excitation energies

## Any questions for the community?
- [ ] Should the Davidson solver from CI and EOM-CCSD (and now here) be standardised throughout the repository, or is it better that the modules remain self-contained?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3847966c550f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.