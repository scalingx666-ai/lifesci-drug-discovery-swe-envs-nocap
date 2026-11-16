# Issue

**Title:** Pin numpy

## Description

<!--
Thank you for sending the PR! We appreciate you spending the time to make BoFire better.

Help us to understand your motivation by explaining why you decided to make this change.

You can learn more about contributing to BoFire here: https://github.com/experimental-desgin/bofire/blob/main/CONTRIBUTING.md
-->

## Motivation

This PR fixes numpy as the new version 2.5.0 released a few days ago has some incompabilities with shap (which uv is not resolving correctly) which are hopefully resolved soon.


### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

Yes.

### Have you updated `CHANGELOG.md`?

No.

## Test Plan
Unit tests.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `85c5d5048fdf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.