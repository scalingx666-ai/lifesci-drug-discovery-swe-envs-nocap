# Issue

**Title:** Weight transform akp

## Description

I fleshed out the capabilities of ampl to handle the `balancing` weights transformer by including the information in the `model_metadata` (in the training dataset part along with `feature_transform_type`), and including `weight_transform_type` (along with `split_uuid`) in the `compare_models.get_filesystem_perf_results()` dataframe. 

After doing this, I also had to expand the parameter parser to accept `None` and `'None'` as options for the `weight_transform_type` because previously the only option in the list was `'balancing'` and this threw errors when trying to predict from a model with 'None' transform type (I'm not sure where the string None came from).

I can still get through all the tutorials without errors so I think this is OK to merge but would like a second pair of eyes!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `befad637955a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.