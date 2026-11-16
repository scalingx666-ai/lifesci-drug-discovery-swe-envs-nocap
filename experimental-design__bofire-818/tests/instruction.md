# Issue

**Title:** Fix Pareto front calculation for reordered pandas columns

## Description

## Motivation

. With pandas 3, selecting output columns in a different order can produce a NumPy array with negative strides, causing `get_pareto_front` to raise in `torch.from_numpy`.

I added a pandas2torch helper to replace the repeated conversion code across the affected files. I kept the four existing regression cases, which check different column orders, automatic and explicit output selection, and filtering of invalid experiments.

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

Yes.

### Have you updated `CHANGELOG.md`?

Yes, under Unreleased / Fixed.

## Test Plan
The test results below are from the original Pareto front fix. I have not rerun the tests after updating the other files.

- Before the fix: the two reordered-column regression cases fail with the reported negative-stride error; the two ordered-column cases pass.
- `pytest tests/bofire/utils/test_multiobjective.py tests/bofire/utils/test_torch_tools.py -q`: 78 passed, 1 skipped.
- Ruff 0.6.5 lint and format checks pass for both changed Python files.
- `ty check bofire/utils/multiobjective.py --python <venv-python>` passes with the CI-pinned ty 0.0.16.
- `git diff --check` passes.

Tested on macOS with Python 3.12.14, pandas 3.0.5, NumPy 2.4.6, PyTorch 2.14.0, and BoTorch 0.18.1. The full multi-platform CI suite was not run locally.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `38bcf0bdb1c4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.