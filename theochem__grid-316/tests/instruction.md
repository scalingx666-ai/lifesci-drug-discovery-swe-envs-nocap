# Issue

**Title:** Fix incorrect parameter names in docstrings

## Description

### Description

Three docstrings documented parameter names that do not match their function signatures:

- `NumericalIntegrand.integrate` (`src/grid/ngrid.py`) documented `integrand`, but the parameter is `integrand_function`.
- `_evaluate_coeffs_on_points` (`src/grid/ode.py`) documented `coeffs`, but the parameter is `coeff`.
- `deriv3` (`src/grid/rtransform.py`) documented `array`, but the parameter is `x`.

This corrects the documented names to match each signature. Documentation-only change.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0e3fe0924860`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.