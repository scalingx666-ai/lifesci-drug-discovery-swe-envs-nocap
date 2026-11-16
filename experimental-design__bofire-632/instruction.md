# Issue

**Title:** Wrapper für Botorch Test Functions

## Description

<!--
Thank you for sending the PR! We appreciate you spending the time to make BoFire better.

Help us to understand your motivation by explaining why you decided to make this change.

You can learn more about contributing to BoFire here: https://github.com/experimental-desgin/bofire/blob/main/CONTRIBUTING.md
-->

## Motivation

BoTorch recently streamlined their API regarding their test functions. In this PR, a wrapper around it is provided. This makes all test functions from botorch directly usable in BoFire. Only restriction: currently it supports only continuous single-objective functions. It will be extended in follow-up PRs. 

After it, there can be also a tidy-up where all benchmark functions that are available both in botorch and bofire can be removed from bofire.

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

Yes.

## Test Plan

Unit tests.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8e70e331cbcd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.