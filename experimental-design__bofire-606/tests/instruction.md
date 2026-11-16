# Issue

**Title:** Additions for Fully Bayesian Models

## Description

<!--
Thank you for sending the PR! We appreciate you spending the time to make BoFire better.

Help us to understand your motivation by explaining why you decided to make this change.

You can learn more about contributing to BoFire here: https://github.com/experimental-desgin/bofire/blob/main/CONTRIBUTING.md
-->

## Motivation

This PR adds the following stuff:
- FullyBayesianLinearSingleTaskGP
- FullyBayesianSignleTaskGP
- Input warping for fully bayesian GPs (there is a bug in botorch regarding the warpinng which is addressed here  and leads to the failure of a test in this PR, in addition the warping feature is not yet in a release of botorch, so addional tests will fail)
- MAP version of the SAASFullyBayesianSingleTaskGP
- SaasFullyBayesianSingleTaskGPSurrogate is rename to FullyBayesianSignleTaskGPSurrogate and by the `model_type` keyword one can switch between a linear kernel, a matern kernel with saas priors and a matern kernel with Hvafner priors.

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

Yes.

## Test Plan

Unit tests.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eeafb3cb6197`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.