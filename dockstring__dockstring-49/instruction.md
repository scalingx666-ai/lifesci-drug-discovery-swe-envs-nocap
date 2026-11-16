# Issue

**Title:** Protonate ligand with OpenBabel

## Description

After refinement with a force field, and before adding partial charges, add hydrogens for pH7 with OpenBabel.

The only changes in the code are defining a protonation function to `utils.py`, importing that function, and calling it after writing the embedded mol to pdb.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4d485b7f8af3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.