# Issue

**Title:** Document the kernel data models

## Description

Fifth package batch of the migration started in #802 (#803 objectives/priors, #806 features, #807 acquisition functions). Drains the `kernels` allowlist to zero — **69 field descriptions and 18 class docstrings**, taking the ratchet from 415 to 328 remaining entries.

## Deduplication

26 of the 69 fields were the same few concepts restated: `lengthscale_prior` and `lengthscale_constraint` on **seven** kernels, `ard` on **six**.

The groupings do not nest — `TanimotoKernel` has `ard` but no lengthscale fields, and the two Wasserstein kernels have the lengthscale fields but no `ard` — so two mixins carry them, `ARDKernel` and `LengthscaleKernel`. Both are plain `BaseModel` mixins rather than `Kernel` subclasses, which is the shape @TobyBoyne asked for in #807: `Kernel` now appears exactly once in every concrete MRO.

Twenty declarations become three descriptions, with no change to serialized output:

```
RBFKernel           ard=True   ls_prior=True   Kernel-in-MRO=1
TanimotoKernel      ard=True   ls_prior=False  Kernel-in-MRO=1
WassersteinKernel   ard=False  ls_prior=True   Kernel-in-MRO=1
LinearKernel        ard=False  ls_prior=False  Kernel-in-MRO=1
```

**Left duplicated on purpose:** `num_categories`, `rank`, `prior` and `var_constraint` on `IndexKernel` and `PositiveIndexKernel` — those two are *siblings* under `CategoricalKernel`, not parent and child, so sharing them would mean adding a class to the categorical taxonomy. Same reasoning for `outputscale_prior`, `kernels` and `offset_prior`, each spanning classes with no suitable common ancestor.

## Claims I derived rather than read

Same flagging as #807, since this is again GPyTorch semantics rather than BoFire's. `bofire/kernels/mapper.py` shows *that* a parameter is forwarded, not what it means, so these came from GPyTorch:

- **`nu`** — that only 0.5/1.5/2.5 are supported is read from the validator, but "0.5 gives a rough, non-differentiable surface, 2.5 a nearly smooth one, larger approaches RBF" is not
- **`rank`** on the index kernels — "a low rank forces the categories onto a few shared dimensions, which regularizes the fit"
- **`power`** on `PolynomialKernel` and `offset_prior` — "how much weight the lower-order terms carry relative to the highest one"
- **`WedgeKernel.angle_prior` / `radius_prior`** — "how different an active candidate is from an inactive one" and "how much the value of an active feature matters relative to whether it is active at all". These are my weakest inferences in the PR; the mapper (`mapper.py:453`) shows only that they are forwarded
- **`DownsamplingKernel`** — that the kernel assumes the approximation improves monotonically with fidelity
- **`SphericalLinearKernel`** — that projecting onto the sphere makes it respond to direction rather than magnitude, hence its suitability for compositions

What I *did* read: `ard` becomes `ard_num_dims=len(active_dims) if ard else None` (`mapper.py:90,115`); priors are mapped with the problem dimensionality via `priors.map(..., d=len(active_dims))` (`mapper.py:92-94`), which is what makes the dimensionality-scaled priors from #803 meaningful here; and `FeatureSpecificKernel.features` resolves through `get_feature_indices` (`bofire/surrogates/botorch.py:105`), the same mechanism documented for `CloneFeature` in #806 — so naming an engineered feature selects every input it contributes.

## Two things to look at separately

- **`InfiniteWidthBNNKernel` redeclares `features`** (`continuous.py:91`) as plain `Optional[List[str]]` where `FeatureSpecificKernel` uses `Optional[NonRestrictedFeatureKeys]`, silently dropping the uniqueness validator. Nothing says whether that is deliberate. Following the `CloneFeature` lesson from #806 I have **not** changed the validation — it gets its own description and this flag.
- **`AdditiveKernel` declared `type` twice**, once before and once after its `kernels` field. Removed, since it is unambiguously redundant.

Still open from #807: **`qMFHVKG.alpha` appears inert**.

## Also

Includes the guard test offered during #807 review: every deprecated acquisition function's `log_variant` must name a real member of `AnyAcquisitionFunction`, so a typo in that string fails the suite rather than surfacing in a warning a user eventually reads.

## Rename candidates

Carried forward: **`ard`** (the acronym means nothing without the description), **`squared`** on the Wasserstein kernels (squared *what*), and **`nu`**.

## Verification

- `pytest tests/bofire/data_models` — 1889 passed, 4 skipped
- `pytest tests/bofire -k "kernel or surrogate"` — 647 passed, 2 skipped
- ruff 0.6.5 clean; `ty==0.0.16` at 158, matching the merged-main baseline

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1f8204db197e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.