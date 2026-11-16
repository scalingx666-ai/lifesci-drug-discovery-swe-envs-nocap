# Issue

**Title:** Updated Perf plots akp

## Description

Instead of digging deeper into the code (transformers) I only fixed how the perf_plots.plot_pred_vs_actual() is rendered by checking for 0's in the weights and fixing the actual_y_values there instead of further back in the code. If it's better, I can work on instead changing untransform() to to fix the mean value data --> zero-centered data transformation issue where nan's are replaced with 0's for regression models.

Additionally, I added a check in the featurization.make_weights() to only replace nan's with 0's if the model_type is classification.

Lastly, I make sure to exclude nan's from model_dataset.get_classes() which returns a set of class labels.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5bc6fc8d4c5f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.