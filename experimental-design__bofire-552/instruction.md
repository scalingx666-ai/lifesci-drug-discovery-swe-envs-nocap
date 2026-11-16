# Issue

**Title:** Documentation on using categorical outputs

## Description

<!--
Thank you for sending the PR! We appreciate you spending the time to make BoFire better.

Help us to understand your motivation by explaining why you decided to make this change.

You can learn more about contributing to BoFire here: https://github.com/experimental-desgin/bofire/blob/main/CONTRIBUTING.md
-->

## Motivation

This PR restructures the `Unknown_Constraint_Classification` notebook and adds some more explanation on how the classification model is integrated into the acquisition function.

Furthermore, also the place in the code where this is taking place was improved from a documentation perspective by improving the comment there.  


### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

Y

## Test Plan

No tests needed, only docs.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2e8b17379d2b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.