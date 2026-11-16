# Issue

**Title:** Improve and fix affinity loss

## Description

Expose additional parameters for the `AffinityLoss`, now available as `--penalty_affinity_loss` and `--scale_affinity_loss` (). The scale parameter is different from the original implementation because it scales the whole loss (it is therefore akin to Caffe's `loss_weight`) instead of only [scaling the gradients in the backward pass](https://github.com/gnina/gnina/blob/6d44ef39bdaa60dc2eaa0d54be13b63b4cf0716d/caffe/src/caffe/layers/affinity_loss_layer.cpp#L126).

Additionally, this PR fixes a bug for which the `--delta_affinity_loss` parameter was used for the affinity L2 loss, while it should only be used for the affinity pseudo-Huber loss. This was causing the affinity L2 loss to be artificially small.

The default parameter `pseudo_huber` has been changed to `False` for consistency with the `--pseudo_huber_affinity_loss` parameter (which is set to `False` by default, in agreement with the original [default2018](https://github.com/gnina/models/blob/de5e9b8e3234b68a959747eec04e34a902474dcb/crossdocked_paper/default2018.model#L271) and the [dense](https://github.com/gnina/models/blob/de5e9b8e3234b68a959747eec04e34a902474dcb/crossdocked_paper/dense.model#L1283) models).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ce377df2e4d1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.