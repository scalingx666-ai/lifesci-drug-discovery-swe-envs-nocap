# Issue

**Title:** Utils function fixes and enhancements

## Description

Fixed curate_data.freq_table so it won't fail when column selected contains NaNs.

Added a new optional boolean argument to base_smiles_from_smiles and rdkit_smiles_from_smiles, useCanonicalTautomers. If set True, the function will perform the additional standardization step of mapping structures to their "canonical" tautomers. The default is False to preserve compatibility with datasets generated previously.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ebd4586450eb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.