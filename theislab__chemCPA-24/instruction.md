# Issue

**Title:** Add chemical representation

## Description

This has become much simpler since we first talked about #15 a few weeks ago. Mainly it just loads the dataframe with the precalculated embeddings, extracts the embeddings for all relevant SMILES in the correct order and converts that to a `torch.nn.Embedding`.

Notes:
- I changed Grover to output just a single dataframe. This means we don't have to specify the dataset when we load the embedding. The dataframe needs to contain all relevant SMILES (LINCS + Trapnell for now).
- So far it doesn't support combinations of perturbations, mainly because I didn't have a dataset with combinations of drugs and SMILES. Incorporating this involves adding ~2 lines.

This PR is based on #23, which should be merged first. I'll go through this PR again tomorrow and add a test or two to make sure the sorting works as intended.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d5767270a712`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.