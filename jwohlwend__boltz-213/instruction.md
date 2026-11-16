# Issue

**Title:** Feat/cyclic offset

## Description

# Description

The purpose of the PR is to implement the cyclic offset positional encoding in Boltz1. Currently, the residue relative positions are computed linearly, meaning that the sequence is assumed to be a linear peptide. However, this relative positioning does not work well in cyclic peptides. As such, this PR applies the cyclical relative position encoding to allow for better prediction of cyclic species as first reported in the [AfCycDesign preprint](https://www.biorxiv.org/content/10.1101/2023.02.25.529956v1.full).

We are showing the result of applying the cyclic offset on the cyclic peptides tested by the AfCycDesign authors (see figure below). We are comparing the RSMD achieved using the standard linear offset with the RSMD achieved using the cyclic offset. The figure shows that for the majority of the peptides the cyclic offset achieved better alignment with the ground truth compared to the linear offset.

![image](https://github.com/user-attachments/assets/5f0fe312-cc36-41d6-8f57-30210fe69651)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5f515995cfca`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.