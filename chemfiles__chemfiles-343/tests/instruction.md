# Issue

**Title:** Rewrite PDB secondary structure reading to use file order of residues

## Description

Fixes issue #342 by rewriting how secondary structures are read in PDB files. Instead of relying on a map with ordered residue information, this PR sets a 'flag' which contains the current residue secondary structure (as a string) and the final residue which has the given secondary structure. This, in effect, causes secondary structures to be read in the same order as the PDB.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2f9d745a97c1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.