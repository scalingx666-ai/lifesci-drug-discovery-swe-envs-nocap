# Issue

**Title:** Fix test failures on main after #831: LKJ in random kernel priors, fit attempts back to 50

## Description

Fixes the two test failures on `main` since #831 (Tests run on `f19d11d5`). Both depend on chance, which is why they passed in #831's own CI.

## 1. `test_map[kernel_spec*]`: `LKJCovariancePrior does not implement mode`

- The kernel specs draw a **random** prior for lengthscales, angles, radii, offsets and powers via `priors.valid().obj()`. That pool includes `LKJPrior`, a prior over correlation matrices that has no `mode`.
- Since #831, hyperparameters start at their prior's mode (`priors.map_constraint`), so mapping a kernel that drew LKJ raised `NotImplementedError`.
- Measured over all kernel specs: 55 errors in 100 rounds before this fix, 0 after.
- **Fix:** `tests/bofire/data_models/specs/kernels.py` draws any valid prior except `LKJPrior` (`_scalar_prior()`).

## 2. `test_pairwise_gp_likelihood[logit]`: `ModelFittingError`

- The pairwise GP with a logit likelihood often fails or warns on its first fit attempt, and BoTorch then retries from random starting values.
- #831 lowered the default retries from 50 to 10.
- Measured with the test's data, over 40 seeds:

  | `max_attempts` | failed fits |
  |---|---|
  | 10 | 7 / 40 |
  | 50 | 0 / 40 |

- **Fix:** `LBFGSB.max_attempts` defaults to 50 again, as before #831. The CHANGELOG entry about the lower default is removed.

## Verification

- Data model, kernel and surrogate tests pass (2250). Ruff clean; `ty` 154 diagnostics, as on `main`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f19d11d57f1d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.