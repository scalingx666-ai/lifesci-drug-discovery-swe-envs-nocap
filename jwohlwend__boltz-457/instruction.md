# Issue

**Title:** Add support for dumping embeddings during prediction

## Description

This pull request introduces functionality to save embeddings (`s` and `z`) during the prediction process and updates the relevant methods and models to support this feature. The changes span multiple files, including updates to the writer class, CLI options, and model outputs.

### Summary

- Implemented way to dump the single and pair embedding representation coming out of the `Pairformer` to `npz` file, following the suggestion in: jwohlwend/boltz#87.
- Added argument to trigger saving embeddings during prediction.

### Issues

Related to issues jwohlwend/boltz#87 and jwohlwend/boltz#280.

### Details

- The `s` and `z` embeddings are added to the returned dictionary in the `forward` and `predict_step` method of both `Boltz1` and `Boltz2` models
- The `BoltzWriter` custom callback is modified to dump the embeddings similarly to what already implemented for other information to save, _e.g._, PAE and PDE.
- Added `--write_embeddings` CLI option to `predict` command in main script to enable saving embeddings, passed this parameter to the writer class in the `predict` function.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `06111a8e09cc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.