# Issue

**Title:** Shap

## Description

<!--
Thank you for sending the PR! We appreciate you spending the time to make BoFire better.

Help us to understand your motivation by explaining why you decided to make this change.

You can learn more about contributing to BoFire here: https://github.com/experimental-desgin/bofire/blob/main/CONTRIBUTING.md
-->

## Motivation

This PR adds Shap Analysis to BoFire surrogates.

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

Yes.

## Test Plan

Unit tests. @jkeupp and @e-dorigatti: could you have a look at the current implementation, and tell me if it looks ok for you. Then I will implement unit tests (so far it is tested only in a notebook). Note that this version is able to deal with categoricals etc.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `51b1078f80c4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.