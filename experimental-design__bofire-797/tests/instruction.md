# Issue

**Title:** fix: make registered engineered features visible to Features.get()

## Description

.

## The bug

Registering a custom engineered feature via `register_engineered_feature` makes Pydantic accept it, but `get()` / `get_keys()` silently omit it.

This is not cosmetic. Every accessor that relies on the default filter degrades, and the failure is silent end-to-end — a surrogate trains **without** the feature and **without** any error or warning:

```
engineered_features.get_keys() : []
n_transformed_inputs           : 0
get_features2idx()             : {}
model train_inputs shape       : torch.Size([10, 3])   ← expected [10, 4]
input_transform                : Normalize()           ← AppendFeatures never attached
```

`validate_inputs()` also becomes a no-op, so a feature referencing a nonexistent input key passes validation.

## Root cause

Three independent defects, all the same underlying mistake: **binding a mutable registry at import time**.

**1. Def-time default binding.** `_BaseFeatures.get()`/`get_keys()` bound `AnyFeature` as a default argument. Python evaluates that once at import and stores it in `__defaults__`:

```python
_BaseFeatures.get.__defaults__[0] is fapi.AnyFeature  # True
```

`tagged_union()` returns a *new* object each call, so rebinding the module global can never reach the default. Worth stating plainly: **the "just rebuild `AnyFeature`" fix alone does not work** — I verified it leaves `get_keys()` returning `[]`.

**2. Stale cross-module import.** `domain/features.py` does `from ...features.api import AnyEngineeredFeature`, so `__add__`'s `is_engineeredfeats` reads a permanently stale union. `EngineeredFeatures(...) + [custom_feat]` raised `union_tag_invalid`.

**3. Registry drift.** `register_engineered_feature` updated `AnyEngineeredFeature` but not `AnyFeature`, so `Features(features=[custom_feat])` raised. `AnyFeature` already lists all nine built-in engineered types, so it was clearly meant to cover them.

## The fix

- **`get()`/`get_keys()`** default to a `_Unset` sentinel and resolve the filter at call time from `model_fields["features"].annotation` — the annotation registration patches in place. Reading the class's generic parameter instead would be equally stale (`__orig_bases__` is frozen at class-creation time).

  A sentinel is required rather than `None`: `includes=None` already means "no include filter" and must keep that meaning. Collapsing the two states would have broken `sobo.py:73` and three existing assertions in `test_features.py`.

- **`__add__`** filters on the `EngineeredFeature` base class, mirroring how `is_infeats`/`is_outfeats` already use `Input`/`Output`.

- **`register_engineered_feature`** keeps `AnyFeature` and `Features.features` in sync, via a new `_FEATURE_TYPES` registry mirroring the existing `_ENGINEERED_FEATURE_TYPES` pattern. It sits inside the block already guarded by `register_into`, inheriting idempotency and duplicate-discriminator handling.

`_Unset` is a class rather than `object()` so it satisfies the `Type` member of the parameter annotation — this lets two now-dead `# ty: ignore[invalid-parameter-default]` directives be dropped without introducing new errors.

## Reviewer note

`get()`'s default now resolves per container: `Inputs.get()` filters by `AnyInput` rather than `AnyFeature`. This is a no-op today — Pydantic already guarantees an `Inputs` container holds only `AnyInput` members — but there are ~59 no-arg `.get()`/`.get_keys()` call sites, so it deserves a deliberate look rather than being buried in the diff.

## Tests

The existing registration tests asserted only `.features` and `len(.features)` — precisely the two things that already worked. That gap is what let this ship.

16 new tests. Verified they fail without the fix: reverting only the source, **8 of 13** failed; reverting only Part A (keeping the rest), **exactly the 3** `AnyFeature` tests failed. The tests that pass in both states are the `includes=None` semantics guards, which is intended — they exist to prove nothing moved.

The end-to-end test fits a real `SingleTaskGPSurrogate` and asserts `train_inputs[0].shape[-1] == 4` (3 raw + 1 appended). That is the silent model corruption, caught directly.

## Validation

| | Result |
|---|---|
| `tests/bofire/data_models` + `test_register.py` | 1423 passed, 5 skipped |
| `tests/bofire/surrogates` + `strategies` | 789 passed, 62 skipped, 2 failed |
| `utils`, `kernels`, `priors`, `outlier_detection`, `plot` | 284 passed |
| `ruff check` / `format` | clean |
| `ty check bofire` | 144 diagnostics, down from 146 on baseline |

The 2 failures are `test_n_zero_eigvals_unconstrained` / `_constrained` in `tests/bofire/strategies/doe/test_utils.py`. I confirmed they fail identically on a clean tree with this change reverted — pre-existing, DoE eigenvalue utilities, unrelated to this PR.

## Known limitations, not addressed here

- `data_models/api.py:70` computes `AnyThing` at import time, so it never sees post-import registrations. This affects **every** registrar (kernels, priors, strategies), not just features. Its only consumer is a schema test that parametrizes at collection, so it is inert today. Worth a separate issue.
- The now-unused `AnyEngineeredFeature` import in `domain/features.py` is still stale after registration. Its remaining uses are a runtime-noop `cast()` and the class generic parameter (which Pydantic resolves into `model_fields`, where registration patches it), so it is harmless — but it is a trap for the next reader. Left alone to keep this diff focused.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `44cf4f0ce89d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.