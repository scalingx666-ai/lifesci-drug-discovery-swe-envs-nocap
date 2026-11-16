# Issue

**Title:** Reintroduce sampling parameter into DoEStrategy to allow for seeding

## Description

## Motivation

Make DoE test fail less often

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

yes

## Test Plan

add retries to (stochastically) failing test

[edit] we ended up fixing the inputs of the optimization instead of adding retries [/edit]

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6885bdbfac1c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.