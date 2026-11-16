# Issue

**Title:** Fix prediction column order for mixed continuous/categorical outputs

## Description

## Motivation

With both continuous and categorical outputs, `predict()` puts values under the wrong column names (#838). The models are stacked in `outputs.get_keys()` order, which sorts continuous outputs before categorical ones, but `get_column_names()` listed all categorical columns first. The arrays are labelled by position, so e.g. a continuous prediction ended up in `phase_pass_prob`.

`get_column_names()` now walks `outputs.get([CategoricalOutput, ContinuousOutput])`, which uses the same sorted order the models are assembled in, so the names follow the model order regardless of `order_id`.

### Have you read the Contributing Guidelines on pull requests?

Yes.

### Have you updated `CHANGELOG.md`?

Yes, under Fixed.

## Test Plan

- Updated the two mixed-output cases in `tests/bofire/utils/test_naming_conventions.py` to the model order; they fail on `main` and pass with the change.
- End-to-end check: a `SoboStrategy` with a `ContinuousOutput` (values around 100) and a two-class `CategoricalOutput`. On `main` the class probabilities summed to ~85 and `f_0_pred` was ~0.3; with the change they sum to 1.0 and `f_0_pred` is ~85-94.
- `pytest tests/bofire/utils tests/bofire/surrogates tests/bofire/strategies tests/bofire/data_models/domain`: 1294 passed, 139 skipped.
- ruff 0.6.5 check/format and ty 0.0.16 clean on the changed files.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `506a49ff1c4b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.