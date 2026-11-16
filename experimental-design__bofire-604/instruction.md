# Issue

**Title:** Feature/exclude constraints in bo

## Description

<!--
Thank you for sending the PR! We appreciate you spending the time to make BoFire better.

Help us to understand your motivation by explaining why you decided to make this change.

You can learn more about contributing to BoFire here: https://github.com/experimental-desgin/bofire/blob/main/CONTRIBUTING.md
-->

## Motivation

This PR introduces the use of `CategoricalExcludeConstraint`s in botorch based BO strategies. Currently it is only supported for fully discrete search spaces. Soon, it will also be available for mixed ones using the botorch acqf optimizer. For this reason, the code for the validator was duplicated, as it will be in the future independent validators, since the two acqf optimizers will support different things there.


### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

Yes.

## Test Plan

Unit tests.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `846333441b62`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.