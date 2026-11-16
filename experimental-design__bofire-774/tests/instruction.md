# Issue

**Title:** Add dimensionality-scaled Gamma priors (CHEN and dim-scaled threesix)

## Description

## Context

BayBE 0.15.0 introduced dimension-aware Gamma hyperpriors in its GP presets — the **CHEN** preset and a new default that scales the lengthscale prior with the problem dimensionality. BoFire already expresses the Hvarfner dimension-scaled prior as a first-class, serializable data model (`DimensionalityScaledLogNormalPrior`) plus the mapper plumbing that passes the problem dimension `d` into lengthscale-prior mapping. This PR adds the Gamma analogues, reusing that same infrastructure — so these priors are serializable prior objects rather than imperative factory code.

## What

- **`DimensionalityScaledGammaPrior`** — Gamma analogue of `DimensionalityScaledLogNormalPrior`:
  ```
  concentration_eff = concentration + concentration_scaling * sqrt(d)
  rate_eff          = rate * d ** rate_power
  ```
  The asymmetric scaling (additive on concentration, power on rate) lets a single class express both target priors exactly.

- **Opt-in prior constants** (no surrogate/kernel defaults change):
  - `CHEN_LENGTHSCALE_PRIOR` = `Gamma(2m, 2)`, `CHEN_OUTPUTSCALE_PRIOR` = `Gamma(m, 1)` with `m = 0.4·√d + 4` — dimension-aware hyperpriors from Chen, Fleck & Stuyver, *"Leveraging Hidden-Space Representations Effectively in Bayesian Optimization for Experiment Design through Dimension-Aware Hyperpriors"*, ChemRxiv 2026, [doi:10.26434/chemrxiv.10001986/v2](https://doi.org/10.26434/chemrxiv.10001986/v2).
  - `DIMENSIONALITY_SCALED_THREESIX_LENGTHSCALE_PRIOR` — keeps the threesix concentration of 3 and scales the rate by `d**-0.5`, calibrated so the lengthscale mode matches the Hvarfner log-normal prior.

- **ScaleKernel plumbing**: `map_ScaleKernel` now forwards `d` (= number of active dims) to the outputscale prior mapping (mirroring `map_PolynomialFeatureInteractionKernel`), and `ScaleKernel.outputscale_prior` is widened from `AnyGeneralPrior` to `AnyPrior` so dimension-scaled priors are accepted there (registered in `priors._rebuild_dependent_models`).

## Testing

- Data-model layer (serialization roundtrip + spec validity) — `tests/bofire/data_models` passes
- Functional mapper + ScaleKernel `d`-threading — `tests/bofire/priors/test_mapper.py`, `tests/bofire/kernels/test_mapper.py`
- Registration coverage (`test_prior_rebuild_covers_all_anyprior_fields`) passes with the new `AnyPrior` field
- `ruff check`/`format` clean; `ty check bofire` reports no new errors

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8905f8d618a6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.