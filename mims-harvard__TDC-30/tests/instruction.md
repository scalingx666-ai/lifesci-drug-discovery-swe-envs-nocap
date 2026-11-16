# Issue

**Title:** Added CRISPR DNA repair outcomes dataset

## Description

**Dataset Description:** Primary T cells are a promising cell type for therapeutic genome editing, as they can be engineered efficiently ex vivo and transferred to patients. This dataset consists of the DNA repair outcomes of CRISPR-CAS9 knockout experiments on primary CD4+ T cells drawn from 15 donors. For each of the 1,521 unique genomic locations from 553 genes, we provide the 20-nucleotide guide sequence along with the 3-nucletoide PAM sequence. 

5 repair outcomes are included for prediction: fraction of indel reads with an insertion, average insertion length, average deletion length, indel diversity, fraction of repair outcomes with a frameshift.

**Task Description**: Given a DNA sequence, predict the repair outcomes of a CRISPR-CAS9 knockout experiment. 

**Dataset Statistics**: 1,521 DNA sequences (guide+PAM) with 5 repair outcomes for each measured across different donor populations of primary T cells

**Dataset Split**: Random Split

**References**: Leenay, Ryan T., et al. "Large dataset enables prediction of repair after CRISPR–Cas9 editing in primary T cells." Nature biotechnology 37.9 (2019): 1034-1037.

**License**: CC BY 3.0.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a87f4ed41add`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.