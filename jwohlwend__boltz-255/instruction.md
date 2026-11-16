# Issue

**Title:** Fixes issue when training Boltz-1x with steering

## Description

As noted by @jbderoo in a comment on PR #249 (and related to #243), training with `fk_steering` and `guidance_update` set to `True` results in a `KeyError`. This is because `compute_constraint_features` is set to `False` by default and couldn't be adjusted from within the training cfg file. 

This minimal PR adds `compute_constraint_features` as an arg to the `DataConfig` and wrapper datasets in `src/boltz/data/module/training.py` so users could train with steering if they want to.  

I'm not sure how useful/practical that would be, but now you can run it at least.

I also added the `compute_constraint_features` arg to the training cfg files, set to the default value of `False` since normally you wouldn't train with steering.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b8b6373842e7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.