# Issue

**Title:** Fixes ligand pLDDTs in PDB/mmCIF b-factor column bugs.

## Description

Ligand pLDDT values are currently incorrectly indexed like polymer pLDDT values when writing PDB and CIF files. 

This patch writes per-atom ligand pLDDTs for relevant atoms into b-factors rather than taking the first atom's plddt (and corrects existing indexing bugs when writing outputs containing multiple ligands []). Reports mean ligand pLDDTs in mmCIF footer (pLDDT qa metric section) rather than taking first atom pLDDT as well (also correcting for the multi-ligand case).

Fixes bug(s) mentioned in #238

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4172e8b45e2b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.