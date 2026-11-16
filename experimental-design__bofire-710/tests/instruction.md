# Issue

**Title:** increase raw noise constraint and remove ScaleKernel

## Description

## Motivation

Reduce overfitting/convergence issues by increasing raw_noise_constraint. Remove ScaleKernel.

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

Yes

## Test Plan

Run old tests, no new tests required.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a9973b18e98e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.