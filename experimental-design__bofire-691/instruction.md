# Issue

**Title:** Exposing various parameters to the user for Random sampling

## Description

## Motivation

The commit exposes advanced sampler parameters to users in [RandomStrategy](https://github.com/KislayaRavi/bofire/blob/scramble/bofire/data_models/strategies/random.py) , allowing fine-grained control over random sampling behavior. Previously, users could only select the sampling method (UNIFORM, SOBOL, or LHS) but couldn't customize method-specific parameters like scrambling or strength settings that are available in scipy's sampling implementations.

Additionally, fixed minor linting issues.

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

Yes

## Test Plan
- Data Model validation tests
- Functional tests added in [test_sampler_kwargs_various_methods](https://github.com/KislayaRavi/bofire/blob/1f5d0a046f4a61525a49a58c6a8a75fb1e8108a6/tests/bofire/data_models/specs/strategies.py#L1027C5-L1027C40) covering five cases involving Uniform sampling, Sobol sampling and Latin hypercube sampling.
- Serialization and deserialization tests are also passing.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c8cd67238677`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.