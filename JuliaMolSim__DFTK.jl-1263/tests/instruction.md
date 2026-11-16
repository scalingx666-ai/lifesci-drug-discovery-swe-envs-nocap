# Issue

**Title:** Add interface and tests for hybrid functionals

## Description

This PR does the following:
- Gets PBE0 working
- Rename `coulomb_kernel_model` to `singularity_treatment`
- Revert default of `AceExx` to `VanillaExx` due to implications to ACE giving virtual orbitals. We should first implement a follow-up SCF step after convergence, which re-diagonalises the Hamiltonian without ACE if ACE is used or be smarter in which orbitals are used for sketching. To be investigated

CC @toschaefer especially regarding the last point.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5fcbdb41f2f5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.