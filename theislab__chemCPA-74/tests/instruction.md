# Issue

**Title:** Fix DE genes for sciplex dataset dependent on available genes

## Description

This PR contrains three parts: 
- Updated notebooks for dataset generation, `lincs_sciplex_gene_matching.ipynb` and `sciplex_SMILES_v1.ipynb` 
- Updated `data.py` to make the key in `adata.uns` a user specified parameter
- Showcase expected behaviour with the manual sweeps contained in `'simon/'`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9866bbbb4be7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.