# Issue

**Title:** Speed up model load by skipping init on strict load

## Description

Model load spends significant time on initializing layers with a slow truncnorm plus an implicit kaiminig_uniform_ of torch.nn.Linear. But this work is discarded at construction when the parameters are overwritten by the actual model weights with load_state_dict.

**Changes**
This commit monkey patches trunc_normal_init_ and nn.Linear's reset_parameters to noops during inference via a skip_random_init context manager.

On my machine, this leads to a reduction of ~1 minute. A similar patch has already been merged into openfold-3 (PR 220).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `01d56deb2180`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.