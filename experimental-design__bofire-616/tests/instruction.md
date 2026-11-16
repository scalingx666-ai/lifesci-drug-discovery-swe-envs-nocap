# Issue

**Title:** number_of_categorical_combinations

## Description

<!--
Thank you for sending the PR! We appreciate you spending the time to make BoFire better.

Help us to understand your motivation by explaining why you decided to make this change.

You can learn more about contributing to BoFire here: https://github.com/experimental-desgin/bofire/blob/main/CONTRIBUTING.md
-->

## Motivation

This PR adds the option to compute the number of categorical combinations, this is needed for the new functionality regarding the alternating optimizer which will follow soon. The method was originally implemented by @TobyBoyne  in  I now made a seperate PR out of it, and will integrate the rest later.

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

Yes.

## Test Plan

Unit tests.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7fb596e0968e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.