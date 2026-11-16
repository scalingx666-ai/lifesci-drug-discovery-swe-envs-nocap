# Issue

**Title:** 595 bug categorical doe unstable

## Description

<!--
Thank you for sending the PR! We appreciate you spending the time to make BoFire better.

Help us to understand your motivation by explaining why you decided to make this change.

You can learn more about contributing to BoFire here: https://github.com/experimental-desgin/bofire/blob/main/CONTRIBUTING.md
-->

## Motivation

[edit Behrang]
The actual problem was a segmentation fault. This has been fixed by checking that smart rounding is only applied if discrete inputs exist. Further, this PR contains additional fixes that were found during debugging.

- A faulty n-choose-k constraint avoided categoricals to be optimized. This has been removed. However, this constraint made sure that the number of experiments was correct. The actual reason for the wrong number of experiments was a wrong formulaic formula. This formula has been fixed.
- Underscores and minus signs in formula strings made problems. Has been fixed by using unambiguous strings instead.
- In the creation of the formula string we have to separate numerical and categoricals because we cannot calculate with categorical.

[/edit]

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

[edit Behrang]
Yes
[/edit]

## Test Plan

[edit Behrang]
Unit tests have been extended.
[/edit]

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5e3a19e127b3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.