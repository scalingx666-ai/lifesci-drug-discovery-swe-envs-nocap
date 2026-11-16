# Issue

**Title:** Combine nchoosek to support variables being shared across nchoosek

## Description

<!--
Thank you for sending the PR! We appreciate you spending the time to make BoFire better.

Help us to understand your motivation by explaining why you decided to make this change.

You can learn more about contributing to BoFire here: https://github.com/experimental-desgin/bofire/blob/main/CONTRIBUTING.md
-->

## Motivation

We have use-cases, where variables need to be subject to multiple nchoosek constraints at once. This is currently not supported.

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

Yes

### Have you updated `CHANGELOG.md`?

yes

## Test Plan

Added three tests to tests\bofire\strategies\test_doe.py

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `53880c990e73`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.