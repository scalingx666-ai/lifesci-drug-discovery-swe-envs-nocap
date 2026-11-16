# Issue

**Title:** add τ in energy_hamiltonian required for some TermXc

## Description

if we use some meta-GGA functional, save and load the scfres with skip_hamiltonian=false (default), it causes energy_hamiltonian to error due to the missing kinetic energy density τ key, despite τ being available in the saved scfres

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ecaf248f6997`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.