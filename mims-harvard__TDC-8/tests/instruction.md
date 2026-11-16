# Issue

**Title:** added drugcomb with nci cell line data

## Description

Added drug combination efficacy data from DrugComb as tested on the the NCI-60 cancer cell lines. For each of the cell lines, I added three genomic features (gene expression, microRNA expression and proteomic profile). This dataset has multiple tasks and can use a cold cell line split.

Dataset Description: This dataset contains the summarized results of drug combination screening studies for the NCI-60 cancer cell lines (excluding the MDA-N cell line). A total of 129 drugs are tested across 59 cell lines resulting in a total of 297098 unique drug combination-cell line pairs. For each of the combination drugs, we provide its canonical SMILES string queried from PubChem. For each cell line, we include the following features downloaded from NCI’s CellMiner interface: 25,723 gene features capturing transcript expression levels averaged from five microarray platforms, 627 microRNA expression features and 3171 proteomic features that capture the abundance levels of a subset of proteins. 

There are two kinds of labels included in this dataset. CSS measures the drug combination sensitivity and is derived using relative IC50 values of compounds and the area under their dose-response curves. The other four metrics capture the synergy between the two drugs. Synergy is a dimensionless measure of deviation of an observed drug combination response from the expected effect of non-interaction. Synergy is calculated using four different models: Bliss model, Highest Single Agent (HSA), Loewe additivity model and Zero Interaction Potency (ZIP).

Task Description: Given the chemical structural information for the combining drugs and genomic features for a particular cell line, predict the drug synergy level or the drug combination sensitivity in that cell line.
Dataset Statistics: 129 drugs are tested across 59 cell lines resulting in a total of 297098 unique drug combination-cell line pairs.
Dataset Split: Random Split, Cold Cell Line Split

from tdc.multi_pred import DrugSyn
data = DrugSyn(name = ‘drugcombo’)
split = data.get_split()

References:
[1] Liu, Hui, et al. "DrugCombDB: a comprehensive database of drug combinations toward the discovery of combinatorial therapy." Nucleic acids research 48.D1 (2020): D871-D881.
[2] Reinhold, William C., et al. "CellMiner: a web-based suite of genomic and pharmacologic tools to explore transcript and drug patterns in the NCI-60 cell line set." Cancer research 72.14 (2012): 3499-3511.

Dataset License: Not Specified. CC BY 4.0.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0f48121bc477`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.