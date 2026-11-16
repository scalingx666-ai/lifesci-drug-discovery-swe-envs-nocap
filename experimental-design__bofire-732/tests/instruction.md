# Issue

**Title:** weightedmean implementation

## Description

## Motivation

Implemented WeightedMeanFeature to support descriptor-based weighted averaging of selected input features, alongside existing engineered feature transforms.

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

Yes

### Have you updated `CHANGELOG.md`?

No, not yet

## Test Plan

Written tests for:

- data model validation of WeightedMeanFeature
- surrogate mapping correctness for WeightedMeanFeature (including explicit expected weighted-mean values)
- weighted-sum surrogate test strengthened with explicit expected-value assertion

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `55fff4acfeb9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.