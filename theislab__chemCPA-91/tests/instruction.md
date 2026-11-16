# Issue

**Title:** Add ability to add layers (extended gene set finetuning)

## Description

This allows adding an extra layer to adjust the input / output dimension. The flag is called `append_ae_layer`.

I also added the all-zero embedding (), and fixed a small bug in the preprocessing.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ec1ab5e4af83`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.