# Issue

**Title:** Fix stochastic test failing

## Description

## Motivation

Need enough samples so the information matrix rank is determined by
structural constraints (e.g. equality constraints), not by sampling luck.
Discrete inputs with few levels are especially prone to degenerate samples
at small N.

Give more headroom so the random samples are diverse enough. There's no deep theoretical reason for exactly 5x — it's a practical choice to reduce the probability of degenerate samples while keeping the computation cheap.

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

Yes

## Test Plan

Fixed stochastic test failing.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ff3f00189436`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.