# Issue

**Title:** Feature/register likelihoods

## Description

<!--
Thank you for sending the PR! We appreciate you spending the time to make BoFire better.

Help us to understand your motivation by explaining why you decided to make this change.

You can learn more about contributing to BoFire here: https://github.com/experimental-desgin/bofire/blob/main/CONTRIBUTING.md
-->

## Motivation

.

We distinguish between MultiTask and SingleTask likelihoods for now, since that is required by the call sites. Maybe following discussion in #860, this can be removed in the future?

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

Yes. This PR is quite Claude-driven, mostly just copying the approach from `kernels.register`.

### Have you updated `CHANGELOG.md`?

Yes

## Test Plan
`TestRegisterLikelihood` and `TestLikelihoodPydanticIntegration`, as done for kernels and priors.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `438869e951f9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.