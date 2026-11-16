# Issue

**Title:** Fixes Boltz-1x related errors encountered during training

## Description

With the recent Boltz-1x update, some issues arose when training new models using `scripts/train/train.py`.

This PR fixes the following and the training code is now working again:

* `steering_args` needed to be included in the training `yaml` configuration files
    * also previously noted by and 
    * I included 1x default `steering_args` with steering and guidance updates set to `False` during training

* issue with the `cyclic_period` field not existing when loading input structure data for training
    * seems like this was because of the new `cyclic_period` field for `structure["chains"]`, which is not available in the training data `npz` files
    * I included a conditional check for this and if it does not already exist, it is populated as `0` and a new structured array for `chains` is used

* `chain_constraint_features` had a local variable issue during training
    * initialized empty `chain_constraint_features` dict in `src/boltz/data/feature/featurizer.py`
    * for consistency with `inference.py` (and maybe needed if you wanted to train with steering turned on?), updated `src/boltz/data/module/training.py` training and validation dataset classes to include the `compute_constraint_features` arg

* the verbose parameter to torch `LRScheduler` is now deprecated (https://discuss.pytorch.org/t/torch-optim-lr-scheduler-py-28-userwarning-the-verbose-parameter-is-deprecated/196634)
    * this parameter was removed in `scheduler.py` to be compatible (since 1x is now using a newer version of `PyTorch`)

* with the 1x update, it seems like the `center_random_augmentation` function was removed from `src/boltz/model/modules/diffusion.py`, which causes a `NameError` when training since the function gets called on line 716
    * this was a simple fix of including it in the `utils` import

* (Note: not related to 1x update) When choosing to set `write_confidence_summary=False` in `main.py`, model ranking by confidence score was not available and errored out
    * being able to set `write_confidence_summary=False` is useful if one is training only the structure module and then testing it before training the confidence module
    * I included a catch in `writer.py` for when `confidence_score` does not exist, where the writer would then default to a linear ranking

I've tested the standard `boltz predict` functionality using a basic example and there were no issues that arose from these changes.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d63e278875cf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.