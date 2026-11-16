# Issue

**Title:** Issue: 680 spherical linear kernel

## Description

## Motivation
This pull request is in response the Issue #680 
Added Spherical Linear Kernel.

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

Yes

## Test Plan
1. PyDantic validation in data model of SphericalLinearKernel.
2. Added test verifying the specs after creation of the object.
3. Testing the mapping to the correct object.
4. Testing if the surrogate is created using SphericalLinearKernel.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c8cd67238677`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.