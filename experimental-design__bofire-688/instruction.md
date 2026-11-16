# Issue

**Title:** Index kernel and Positive Index kernel

## Description

## Motivation
There are two major modifications:
- Added two new kernels to handle categorical and discrete variables:
  - [Index Kernel](https://docs.gpytorch.ai/en/latest/_modules/gpytorch/kernels/index_kernel.html)
  - [Positive Index Kernel](https://botorch.readthedocs.io/en/stable/_modules/botorch/models/kernels/positive_index.html) 
- Added feature in MixedSingleTaskGPSurrogate that allows user to allocate different types of kernels according to the feature name using a kernel dictionary. Earlier all categorical variables and all continuous variables had same type of kernel.

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?
Yes

## Test Plan

- Added both unit tests and integration tests,
- Added PyDantic variable checks.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d3044491ed8d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.