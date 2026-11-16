# Issue

**Title:** Spin adapted CCSD helper functions for linear response function

## Description

I have added the following spin adapted helper functions: 
1. CCENERGY - CCSD energy, T1 and T2 amplitudes
2. CCHBAR - Builds similarity transformed CCSD hamiltonian pieces
3. CCLAMBDA - solves CCSD lambda equations( L1 and L2)
4. CCPERT - solves for X (field perturbed T amplitudes) and Y (field perturbed L amplitudes)
5. CCRESPONSE - calculates dipole polarizability linear response function

The code works as of now but needs some further edits.

1. use lambda and T amplitudes to construct coupled cluster densities
2. more documentation and references for all sections
3. make the perturbation general - dipole, magnetic etc and extension to other similar properties
4. cleanup of the code to make it elegant

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0c98eea7e825`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.