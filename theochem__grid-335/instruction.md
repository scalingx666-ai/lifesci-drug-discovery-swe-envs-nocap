# Issue

**Title:** Fix 1D Cartesian orders in generate_orders_horton_order

## Description

.

`generate_orders_horton_order(order, "cartesian", dim=1)` returned `np.arange(0, order + 1, dtype=np.int)`:
- **It crashes on current NumPy.** `np.int` was removed in NumPy 1.24, so `Grid.moments(..., type_mom="cartesian")` on a grid with points of shape `(N, 1)` raised `AttributeError`.
- **The shape is wrong.** It returns every order from 0 to n instead of the single row `[n]` that the 2D and 3D branches return, so the `np.vstack` in `Grid.moments` couldn't stack the rows even with a valid dtype.

The fix returns `[[order]]` for `dim=1`, like the other dimensions.

### Tests
- `test_generate_orders_horton_order_cartesian_one_dimension` covers the function directly.
- `TestGrid1D.test_cartesian_moments` checks the moments up to order 3 against sums computed by hand.

Both fail on `master` and pass with the change. The full suite passes locally: 640 passed, 1 skipped. Black and ruff report nothing new in the touched files.

I used Claude to help find this and draft the tests. I went through the change and ran the suite myself.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e50e31c9c35c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.