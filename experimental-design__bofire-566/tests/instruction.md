# Issue

**Title:** Use Seed Sequences for random number generation

## Description

## Motivation

Currently, when generating random numbers, the `RandomStrategy` uses a `np.random.Generator` object to sample a random seed. The best practice for generating sequences of seeds is [`np.random.SeedSequence`](https://numpy.org/doc/2.2/reference/random/bit_generators/generated/numpy.random.SeedSequence.html). This PR now uses this in `Strategy`.

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

Yes

## Test Plan

All tests pass for `tests/bofire/strategies/test_random.py`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7d93cb0a369b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.