# Issue

**Title:** Extended metrics

## Description

## Changelogs
- Added boolean option `public` to upload dataset/benchmark/result with public access.
- Added attribute `direction` of the metric  
- Added attribute `args` for additional parameters for the metrics such as `average` method for multiclass tasks.
- Extended `Metric` with  "r2","spearman", "pearsonr", "explained_var" for regression task and  "f1", "roc_auc", "pr_auc", "mcc", "cohen_kappa" for binary/multiclass classification, "f1_macro", "f1_micro" for multiclass task.  #46

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8da092f3bcc2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.