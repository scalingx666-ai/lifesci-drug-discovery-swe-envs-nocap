# Issue

**Title:** add support for categorical input as fixed input in plot gp_slice

## Description

This PR addresses issue #743 

## Motivation

plotting a gp slice so far only supported `ContinuousInput`, it now also allows for `CategoricalInput` for fixed features.

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

yes

### Have you updated `CHANGELOG.md`?

yes

## Test Plan

Added an additional test case for a fixed CategoricalInput

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `19c6f2549456`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.