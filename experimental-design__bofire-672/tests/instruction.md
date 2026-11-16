# Issue

**Title:** Tests/reduce disk space

## Description

<!--
Thank you for sending the PR! We appreciate you spending the time to make BoFire better.

Help us to understand your motivation by explaining why you decided to make this change.

You can learn more about contributing to BoFire here: https://github.com/experimental-desgin/bofire/blob/main/CONTRIBUTING.md
-->

Our tests in the pipeline run out of disc space. Check what packages are not necessary. Torch with CUDA is a candiate to be replaced by CPU-Torch.

Further, I cleaned a little up by removing uv from the workflow which is not really needed there and by removing the xgb option from workflow installations that does not exist anymore.

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

Y

## Test Plan

not applicable

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e719dd68cc56`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.