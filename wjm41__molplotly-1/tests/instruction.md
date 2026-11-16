# Issue

**Title:** Rokas slider

## Description

Implemented support for specifying multiple smiles in the smiles_col argument for molplotly.add_molecules:

- When a single str argument is passed to smiles_col, the function behaves as before.
- When a list is passed, a slider is created under the plot, which allows the user to decide which column to use to render molecules.

Also changed the ports in the example.ipynb to start from 8700 and go up. On my system 8000 and 8001 were reserverd already.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `93b5d8371d0e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.