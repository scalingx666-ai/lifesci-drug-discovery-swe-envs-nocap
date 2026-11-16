# Issue

**Title:** Add notebooks to align genes in sciplex and lincs datasets

## Description

Requirements are mentioned in the respective notebooks. First run the gene_matching notebook. Subsequently, add smiles strings. Added the `PROJECT_DIR` to the paths file. Resulting h5ad files are stored in `'PROJECT_DIR/datasets/'`.

Related to #34

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cd42bd46096a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.