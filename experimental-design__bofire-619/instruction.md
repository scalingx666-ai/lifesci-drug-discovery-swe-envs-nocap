# Issue

**Title:** Update for botorch 0.15.0

## Description

<!--
Thank you for sending the PR! We appreciate you spending the time to make BoFire better.

Help us to understand your motivation by explaining why you decided to make this change.

You can learn more about contributing to BoFire here: https://github.com/experimental-desgin/bofire/blob/main/CONTRIBUTING.md
-->

## Motivation

This PR removes some safeguards in the code and the tests that were in due to features not yet present in the latest botorch release. They are now in the latest release and we can remove the guards by enforcing dependency on botorch 0.15.0

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

Yes.

## Test Plan

Unit tests

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0307f8e7a092`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.