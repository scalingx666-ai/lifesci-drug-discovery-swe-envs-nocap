# Issue

**Title:** InterpolateFeature

## Description

<!--
Thank you for sending the PR! We appreciate you spending the time to make BoFire better.

Help us to understand your motivation by explaining why you decided to make this change.

You can learn more about contributing to BoFire here: https://github.com/experimental-desgin/bofire/blob/main/CONTRIBUTING.md
-->

## Motivation

This PR introduces the `InpterpolateFeature` which makes the `PiecewiseLinearGPSurrogate` obsolete, as this can now be out of the box configured for any kind of GP. 

@Jimbo994: can you review this PR and also test if you can get it running in the same setup as `PiecewiseLinearGPSurrogate`? Then we could also get rid of this one in a seperate PR.

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

Y.

## Test Plan

Unit tests.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c81e8e7e072e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.