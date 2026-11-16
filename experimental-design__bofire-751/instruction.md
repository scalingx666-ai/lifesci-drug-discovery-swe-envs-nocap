# Issue

**Title:** Add Pathwise Thompson Sampling Acquisition Function

## Description

<!--
Thank you for sending the PR! We appreciate you spending the time to make BoFire better.

Help us to understand your motivation by explaining why you decided to make this change.

You can learn more about contributing to BoFire here: https://github.com/experimental-desgin/bofire/blob/main/CONTRIBUTING.md
-->

## Motivation

This PR adds the pathwise Thompson Sampling ACQF to BoFire which is based on Matheron Samples.

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

Yes.

### Have you updated `CHANGELOG.md`?

Yes.

## Test Plan

Unit tests, currently failing since it is not yet in BoFire main, so we should wait with merging it until it is in BoFire main. But we can review it already before.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0f992a125d16`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.