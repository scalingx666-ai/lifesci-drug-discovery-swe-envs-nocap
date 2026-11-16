# Issue

**Title:** Normalize with engineered feats

## Description

## Motivation

In #678, bounds were no longer provided to input transforms, and were instead learned from data. This was done to avoid explicitly providing the bounds of the engineered features.

However, this caused issues in #705, since I required an input to be strictly within the bounds [0, 1], but it was often scaled beyond that value if the training data didn't cover the full space. So instead, we revert back to the original behaviour for regular continuous features, and only learn the bounds for engineered features.

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

Yes

## Test Plan

I have adapted the existing test cases to verify the correct behaviour.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8826796a3ab4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.