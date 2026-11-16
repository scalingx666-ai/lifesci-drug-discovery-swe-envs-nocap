# Issue

**Title:** True nchoosek support for doe

## Description

<!--
Thank you for sending the PR! We appreciate you spending the time to make BoFire better.

Help us to understand your motivation by explaining why you decided to make this change.

You can learn more about contributing to BoFire here: https://github.com/experimental-desgin/bofire/blob/main/CONTRIBUTING.md
-->

## Motivation

Add true nchoosek support to DoE. Features added:

1. n_min and n_max are fullfilled
2. none_also_valid=True is supported
3. variables in nchoosek can have arbitrary bounds (no zero included) 

These are needed to support use cases.

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

Yes.

### Have you updated `CHANGELOG.md`?

Yes.
- Generalized NChooseK constraint support in DoE: `min_count > 0` is now supported, non-zero lower bounds (`lb > 0`) are allowed for NChooseK features, and `nchoosek_constraints_as_bounds` generates deactivation patterns for all activity levels `k ∈ [min_count, max_count]`.

## Test Plan

Added three tests to tests\bofire\strategies\test_doe.py

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `671351fd136a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.