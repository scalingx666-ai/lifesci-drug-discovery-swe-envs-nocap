# Issue

**Title:** Hotfix Acqf setup for fixed-features

## Description

<!--
Thank you for sending the PR! We appreciate you spending the time to make BoFire better.

Help us to understand your motivation by explaining why you decided to make this change.

You can learn more about contributing to BoFire here: https://github.com/experimental-desgin/bofire/blob/main/CONTRIBUTING.md
-->

## Motivation

This PR fixes the issue that when infeasibles are excluded in acqf setup but all are infeasibles an error is raised. Especially with fixed features that can happen often. For this reason, only a warning is now raised. In the future, we can have there a more fine-grained control.


### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

Yes.

## Test Plan

Unit tets.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `37cf73059ecb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.