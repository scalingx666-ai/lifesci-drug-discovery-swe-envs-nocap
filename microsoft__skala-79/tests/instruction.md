# Issue

**Title:** test: de-flake finite-difference gradient checks

## Description

## Problem
`test_density_veff` failed in CI:
https://github.com/microsoft/skala/actions/runs/27552110518/job/81441338475?pr=77#step:5:233

```
assert torch.all(check_mat)
E   assert tensor(False)
```

The check tied its tolerance to Ridders' **per-element** finite-difference error
estimate (`(ana - num).abs() <= max(2**12 * num_err, ...)`). That estimate is a
heuristic and occasionally underestimates the true error; when `num_err` for a
component is anomalously tiny, the bound collapses below the genuine numerical
noise floor and the test flakes (here: difference `3.7e-10` vs collapsed bound
`~2.8e-10`), even though nothing is actually wrong.

## Fix
- **Migrate `test_density_veff` and `test_grid_weights_gradient`** to a fixed
  `torch.allclose(rtol=1e-6, atol=1e-8)`. These gradients are well-conditioned
  (components match the FD reference to ~1e-10..1e-12), so a fixed tolerance is
  robust and immune to the Ridders-estimate flake. Comments document why.
- **Keep the Ridders per-element bound for `test_grad_veff` and `test_kin_veff`.**
  These have large-magnitude components whose coarse finite-difference reference
  is only accurate to ~2% / ~2e-4 relative; a uniform `torch.allclose` would need
  an `rtol` so loose it would stop checking the well-conditioned components. The
  per-element estimate keeps the tolerance tight where the reference is good and
  loose only where it is genuinely coarse. Comments explain this.

### Drive-by cleanups (same Ridders helper)
- Fix typo `num_dif_ridders` -> `num_diff_ridders`.
- Rename the loop variable `iter` (shadowed the builtin) to `i`.

Applied in both `tests/test_pyscf_gradients.py` and `tests/test_gpu4pyscf_gradients.py`.

## Verification
- `ruff format` / `ruff check` clean.
- All four affected tests (12 params) pass locally:
  `test_grid_weights_gradient`, `test_density_veff`, `test_grad_veff`, `test_kin_veff`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c07796ce4d57`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.