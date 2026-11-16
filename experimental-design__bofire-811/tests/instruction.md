# Issue

**Title:** feature: Added shap feature for categorical ouput

## Description

## Motivation

Extend SHAP feature importance to support `CategoricalOutput`. The implementation explains every category probability and supports multiclass and mixed continuous/categorical output predictors while preserving category names when combining explanations.

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

yes

### Have you updated `CHANGELOG.md`?

yes

## Test Plan

Added tests in `tests/bofire/surrogates/test_feature_importance.py` to:
- test shap value calculation for a three-category categorical output and,
- test mixed  continuous/categorical output.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1f8204db197e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.