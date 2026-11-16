# Issue

**Title:** Formulation and SpuriousFeature Wrappers

## Description

<!--
Thank you for sending the PR! We appreciate you spending the time to make BoFire better.

Help us to understand your motivation by explaining why you decided to make this change.

You can learn more about contributing to BoFire here: https://github.com/experimental-desgin/bofire/blob/main/CONTRIBUTING.md
-->

## Motivation

This PR adds two benchmark wrappers:

- `SpuriousFeaturesWrapper`: it introduces features to a given benchmark that are not taken into account in the evaluation. It is a generalized form of the Branin30 benchmark function. In a tidy-up (maybe at the next Hackathon). Branin30 can also be removed.
- `FormulationWrapper`: it wraps a benchmark problem into a formulation problem by adding additional spurious features to fill up the sum constraint.

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

Y.

## Test Plan

Unit tests.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0eb26663b10b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.