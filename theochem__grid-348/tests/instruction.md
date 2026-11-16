# Issue

**Title:** Fix HandyModRTransform.deriv3 for m > 2

## Description

`HandyModRTransform.deriv3` had `2 * two_m` in the first term of the numerator where the analytic third derivative has `two_m**2`. That term is multiplied by `(m - 1)(m - 2)`, so it only goes wrong for `m >= 3`, and the existing tests all use `m <= 2`. The bad value also propagates to `deriv3_inverse` and to `solve_ode_ivp` / `solve_ode_bvp` on third-order ODEs with this transform (e.g. `y''' = 6` with `m = 3` was about 10% off the exact `(x + 0.5)**3`; it now matches).

Changes:
- `rtransform.py`: `2 * two_m` -> `two_m**2` in `HandyModRTransform.deriv3`.
- `test_transform.py`: `test_handymod_deriv3_matches_finite_differences`, checking `deriv3` against the existing finite-difference helper for m = 1 to 5.

Testing:
- The new test fails on master for m = 3, 4, 5 and passes with the fix.
- I also checked `deriv3` against the sympy third derivative of `transform` for m = 1 to 5 (relative error ~1e-15 after the fix), and reran the `solve_ode_ivp` example from the issue.
- `pytest src/grid/tests/test_transform.py src/grid/tests/test_rtransform.py src/grid/tests/test_ode.py` passes (317 passed).
- Black and ruff report nothing new in the touched files.

I used Claude to help find the bug and draft the test; I reviewed the change and ran the tests myself.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e742be1e23c9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.