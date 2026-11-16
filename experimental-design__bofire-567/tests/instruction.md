# Issue

**Title:** bounds can be tuple

## Description

<!--
Thank you for sending the PR! We appreciate you spending the time to make BoFire better.

Help us to understand your motivation by explaining why you decided to make this change.

You can learn more about contributing to BoFire here: https://github.com/experimental-desgin/bofire/blob/main/CONTRIBUTING.md
-->

## Motivation

Static type checkers will not complain if bounds are defined as tuples with two elements. With this change, lists and tuples can be used without complaints of static type checkers.

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

Y

## Test Plan

Should not have an impact on the runtime behaviour. Just a change of a type annotation.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `65bbe90c265c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.