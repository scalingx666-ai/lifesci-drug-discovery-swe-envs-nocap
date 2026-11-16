# Issue

**Title:** Move Conditional Features tutorial to Quarto docs

## Description

## Motivation

In PR #645, I added a tutorial for the new conditional input features as a .ipynb. Since then, all tutorials have been moved to Quarto, except this one. We can now delete the root level `tutorials` folder.

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

Yes

## Test Plan

N/A

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `58a017523ecb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.