# Issue

**Title:** Fix promptsmiles

## Description

Fixed a bug in with PromptSMILES, the reward should always be computed on the final completed SMILES which may be different to the actions used to update the model.

Other things were pre-commit

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `88f562ab05d6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.