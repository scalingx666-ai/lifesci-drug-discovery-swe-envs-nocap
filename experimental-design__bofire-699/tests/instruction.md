# Issue

**Title:** Pin pandas to 2.3.3

## Description

<!--
Thank you for sending the PR! We appreciate you spending the time to make BoFire better.

Help us to understand your motivation by explaining why you decided to make this change.

You can learn more about contributing to BoFire here: https://github.com/experimental-desgin/bofire/blob/main/CONTRIBUTING.md
-->

## Motivation

A new pandas version (3.0.0) was released yesterday, currently this creates problems with @formulaic which needs to be investigated. For the meantime, we fix it to <= 2.3.3

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

Yes.

## Test Plan

Unit tests.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a970b5f94d4f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.