# Issue

**Title:** 652 decorrelated mol features

## Description

## Motivation

Issue number 652: 
Problem: When using molecular descriptors for molecular optimization, many descriptors are highly correlated, leading to redundant information.

Solution: Provides automated correlation-based filtering to select a minimal set of informative, uncorrelated descriptors. First remove the descriptors with zero variance and then remove the highly correlated descriptors. 

Additionally: The mordred descriptors names is now set dynamically instead of having a static set of fixed names.

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

Yes.

## Test Plan

1. Unit test with realistic molecular data (37 brominated compounds): Validates that filtering works correctly across all Mordred descriptors.
2. Type safety enforced through Pydantic validators (runtime validation)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6a4d3175c015`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.