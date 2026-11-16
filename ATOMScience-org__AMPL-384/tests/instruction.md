# Issue

**Title:** Add compute_drug_likeness function to rdkit_easy

## Description

Add a function to the rdkit_easy module to compute various drug-likeness criteria for compounds in a data frame (Lipinski rule of 5, Ghose and Veber filters, QED), along with the descriptors used to derive them.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eadd9d4f226c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.