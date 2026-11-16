# Issue

**Title:** Fix jacobian and hessian evaluation for list expressions

## Description

<!--
Thank you for sending the PR! We appreciate you spending the time to make BoFire better.

Help us to understand your motivation by explaining why you decided to make this change.

You can learn more about contributing to BoFire here: https://github.com/experimental-desgin/bofire/blob/main/CONTRIBUTING.md
-->

## Motivation

Hi Johannes, when working on nonlinear constraints I have noticed that two tests were failing, my guess it is due to `pandas.eval()` and `numexpr` compatibility issues with list expressions in Python 3.13.
The tests in question: 
- `test_nonlinear_constraints_jacobian_expression`
- `test_nonlinear_constraints_hessian_expression`

Cause analysis: 
The `jacobian()` and `hessian()` methods were attempting to evaluate string expressions containing list literals such as `"[2*x1, 2*x2, -1]"` - directly with `pandas.eval()`. 
When doing so you get error message: 
`ValueError: setting an array element with a sequence` due to inhomogeneous array shapes.

At first I created an issue, but then I made a few modifications to the nonlinear.py and now tests pass - I hope these fixes are good enough. 
Both for Jacobian and Hessian we first detect list/nested list expressions, then these components are evaluated separately and we handle all the scalars by pushing them to all rows. Not sure if using dataFrame was a good call. 

## Changes
- **`jacobian()`**: Added parsing for list expressions like `"[2*x1, 2*x2, -1]"`
- **`hessian()`**: Added parsing for nested list expressions like `"[[6*x1, 0, 0], [0, 2, 0], [0, 0, 0]]"`

All other tests in the constraints also passed, and we maintain compatibility with Callable expressions and backward one for non-list expressions


### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

yes, but I am a new contributor

### Have you updated `CHANGELOG.md`?

no

## Test Plan

I would run: pytest tests/bofire/data_models/constraints/test_nonlinear.py -v
Or if you want to test all tests run: pytest tests/bofire/data_models/constraints/ -v

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a24b03db12c6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.