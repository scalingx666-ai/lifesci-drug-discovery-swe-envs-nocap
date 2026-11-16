# Issue

**Title:** fix: MultiExp negative weights and inf/nan at end points

## Description

Fixes the `Multi Exp` problems reported in #265.

**Problem 1: negative weights.** `MultiExpRTransform` maps [-1, 1] to [infinity, rmin], so dr/dx is negative. `BaseTransform.transform_1d_grid` multiplied the 1D weights by the signed derivative, so every radial weight was negative and integrals flipped sign (the Multi Exp rows in the issue have the same magnitude as Knowles, only negated).

**Problem 2: inf / nan at end points.** `MultiExpRTransform.transform/deriv/deriv2/deriv3` ignored `trim_inf`, so 1D grids that contain x = -1 (Trapezoidal, Simpson, Clenshaw-Curtis, Gauss-Chebyshev-Lobatto, tanh-sinh) gave `inf`/`nan` weights, which are the `-inf` and `nan` rows in the issue. Becke, Knowles and the others already trim the infinity.

**Changes**
- `transform_1d_grid` uses `|dr/dx|` for the weights (unchanged for transforms that increase with x). `deriv` itself is untouched since the inverse-derivative formulas rely on its sign. Docstring updated.
- `MultiExpRTransform` now applies `_convert_inf` when `trim_inf=True` and suppresses the divide-by-zero warning at the end point, like the other transforms.

**Result** (issue script, Ne promolecule, 151 points, `r_max=4`): all 66 grid/transform combinations are now finite, and Multi Exp gives the same errors as Knowles (best `7.5e-5`, Midpoint). No Multi Exp row is negative, inf or nan any more.

**About the other numbers in the issue**
- The huge errors (1e5 to 1e75) for Becke/Handy/Knowles are gone on current master.
- Linear Finite and Handy Mod stay at about `3.4e-3`: with `r_max=4` they drop the charge beyond r=4, which is `3.31e-3` for this density. With `r_max=8` or more they are about `1.3e-4`.
- The `1.3e-4` floor of the best combinations is the dataset: a dense radial integral of the Gaussian Ne density gives `9.99986794`, not 10. It is independent of the angular grid and the number of radial points.

**Tests**
- `test_transform_integral_consistency` used the signed derivative on both sides, so it passed with the bug; it now uses `|dr/dx|`.
- New: positive weights and the exact `exp(-r)` integral for every valid transform; all 11 1D grids x 6 transforms (finite, non-negative weights, `r^2 exp(-r)` integral); MultiExp derivatives at x = -1. These fail on unmodified master (16 failures).
- Full suite: 715 passed. The 6 `test_periodicgrid.py::test_get_item` failures also occur on unmodified master. The one failed CI job was a flaky ODE test (`test_ode`, Python 3.10), which doesn't use `transform_1d_grid`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5201937ab633`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.