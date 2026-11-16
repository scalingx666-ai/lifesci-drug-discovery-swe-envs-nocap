# Issue

**Title:** Fixing is_class Determination in featurization.py

## Description

Hi, when running a multitask classification model, the NaNs in `out_vals` were not being replaced with zeros in the make_weights function in `featurization.py`. The root cause was that the `is_class` variable was incorrectly determined based on `params.model_type` instead of `params.prediction_type`, causing it to always return False and consequently not replacing the NaNs in `out_vals`.
 
I corrected the `is_class` assignments in `featurization.py` to ensure they reflect the `prediction_type`. I ran the multitask classification tests for `atomsci/ddm/test/integrative/delaney_Panel`, which initially passed even without the changes. However, after closer inspection, I found that there were no NaNs in the response columns of test data, which is why the tests passed. When I introduced NaNs into the response columns, the models failed to train with the old code. After applying the `is_class` fix, the models trained successfully.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `745680929d5a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.