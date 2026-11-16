# Issue

**Title:** Fix/conditional kernel hyperparameters

## Description

## Motivation

Some minor fixes to how the conditional kernel works. In roughly decreasing order of significance:
1. WedgeKernel now properly handles `active_dims` not being the full set of features.
2. `ard=True` now works for WedgeKernel
3. Change radius to inverse radius, so that the same priors can be used as for lengthscale (which is an inverse length).
4. Removed the non-rotated embedding.

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

Yes

### Have you updated `CHANGELOG.md`?

No - I think these are all pretty minor all round, essentially just bugfixes. No API changes. Very minor change of how the `radius` parameter is interpreted.

## Test Plan

Tests written to check dimension handling and mapping.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `506a49ff1c4b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.