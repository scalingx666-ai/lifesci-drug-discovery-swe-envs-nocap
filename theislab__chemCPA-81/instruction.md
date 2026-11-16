# Issue

**Title:** Create 3 ood splits that exclude drugs of 3 different pathways

## Description

Ref. #77 
The gene alignment is also updated - to macht all genes and the gene subset to lincs genes. For the ood split an additional notebook is added that excludes drugs based on their tanimoto similarity. The output file is called `lincs_complete.h5ad`.

Ref. #78
The larger gene set is now the default `'trapnell_cpa(_lincs_genes.h5ad'` and the subset to lincs genes is still called `'trapnell_cpa_lincs_genes).h5ad'`

@siboehm, I excluded less genes in the end (4/3 per pathway) as the sciplex dataset does not contain that many drugs in each pathway. These are, however, true ood drugs - opposed to including them when their were applied in small doses.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0bea9908bc4e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.