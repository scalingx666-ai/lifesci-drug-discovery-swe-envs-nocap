# Issue

**Title:** replace .json() with .model_dump_json()

## Description

<!--
Thank you for sending the PR! We appreciate you spending the time to make BoFire better.

Help us to understand your motivation by explaining why you decided to make this change.

You can learn more about contributing to BoFire here: https://github.com/experimental-desgin/bofire/blob/main/CONTRIBUTING.md
-->

## Motivation

Deprecation warnings do not look good and using deprecated stuff can lead to things breaking at some point

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

yes, with great care and pleasure

## Test Plan

it is a simple change covered by running the notebooks and unit tests

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4d4c136ac4c2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.