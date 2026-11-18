# Issue

**Title:** nci: keep per-atom charges from Mol/SDF/SMILES, ignore quick with nci_detect

## Description

Charge-based NCIs (cation–π, ionic) were missed on two load routes because xyzgraph's site rules read per-atom `formal_charge`/`valence`, which these graphs lacked:

- `load(rdkit_mol, nci_detect=True)`: file-bond graphs now carry the input's per-atom formal charges (RDKit Mol, SMILES, MOL/SDF) and a bond-order `valence`.
- `load(..., quick=True, nci_detect=True)`: `quick` is ignored, since bond-order optimisation is where xyzgraph assigns charges. `bo=False` still hides bond orders when drawing.

Inputs without per-atom charges (mol2, PDB, CJSON) behave as before. Lock bumped to xyzgraph 1.7.0.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `828e721e40b1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.