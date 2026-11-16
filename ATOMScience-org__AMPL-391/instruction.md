# Issue

**Title:** external_training_data parameter was unused

## Description

The external_training_data parameter in `predict_from_model.predict_from_model_file` was unused because it updated `model_pipeline.param` when model_pipeline uses `model_pipeline.orig_param` to load the dataset used to calculate AD indexes.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `65ec4da50e21`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.