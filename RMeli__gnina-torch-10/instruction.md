# Issue

**Title:** Automatic (dynamic) learning rate update on plateau of the loss function

## Description

Add learning rate reduction using `torch.optim.lr_scheduler.ReduceLROnPlateau`.

In contrast with the Caffe implementation, this implementation does not provide early stopping (yet).

Other key differences is that the learning rate update is based on the loss function of the test set (instead of the training set) and that this evaluation is performed based on epochs (instead of iteration). These details might change in future PRs.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `91d8280b3490`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.