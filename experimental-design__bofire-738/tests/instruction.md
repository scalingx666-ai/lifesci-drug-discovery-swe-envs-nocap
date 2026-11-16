# Issue

**Title:** allow only one descriptor

## Description

## Motivation

Was using the `WeightedMeanFeature` on `ContinuousDescriptorInput`s with only one descriptor, and was running into Pydantic Validation errors because we set `Descriptors` to have `min_length=2` is there a specific reason for this @jduerholt or can we simply alter this as I suggested?

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

Yes

### Have you updated `CHANGELOG.md`?

No

## Test Plan

Run current tests. Ran locally without issues.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `95e1a2c2fa64`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.