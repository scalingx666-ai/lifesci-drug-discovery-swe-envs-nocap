# Issue

**Title:** Sweep `sciplex_hparam`

## Description

. 

Preliminary sweep for further experiments #84 and #85.

Add a yaml file for the fine-tuning sweep on the sciplex dataset. 
- hparams that are not swept over come from `lincs_rdkit_hparam`
- hparams that are fixed per drug embedder come from `lincs_all_embeddings_hparam`
____
- [x] Runs started
- [x] Runs finished

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `10529dcfbd09`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.