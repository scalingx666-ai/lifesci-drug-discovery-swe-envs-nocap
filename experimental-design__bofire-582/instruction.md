# Issue

**Title:** CategoricalExcludeConstraint

## Description

<!--
Thank you for sending the PR! We appreciate you spending the time to make BoFire better.

Help us to understand your motivation by explaining why you decided to make this change.

You can learn more about contributing to BoFire here: https://github.com/experimental-desgin/bofire/blob/main/CONTRIBUTING.md
-->

## Motivation

This PR adds a `CategoricalExcludeConstraint`. It can be used to model that certain categorical combinations cannot be used together. Currently, it is only implemented in the `RandomStrategy`. It is influenced by BayBe's `DiscreteExcludeConstraint`.

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

Y

## Test Plan

Unit tests.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7cd49fcc1ba9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.