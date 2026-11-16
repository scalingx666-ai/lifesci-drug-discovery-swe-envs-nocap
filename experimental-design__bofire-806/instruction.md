# Issue

**Title:** Document the features data models

## Description

Third package batch of the migration started in #802 and continued in #803. Drains the `features` allowlist to zero — **41 field descriptions and one class docstring** (`CategoricalOutput`), taking the ratchet from 501 to 459 remaining entries.

## A counting correction worth knowing for the remaining packages

30 of the 41 were harvestable, not the 15 I estimated when picking this package. `engineered_feature.py` documents its fields under Google **`Args:`** blocks rather than `Attributes:`, which an `Attributes:`-only scan misses entirely. Both block types are harvested and removed here, and the scan for the remaining packages should look for both.

## Inheritance: nothing hoisted, and that is the finding

#803 moved `w` to `Objective` and `initial_value` to `PriorConstraint`. This package is the opposite case — I checked every redeclaration and all of them are deliberate type changes that must stay:

| field | why it stays duplicated |
|---|---|
| `unit` | on the numerical inputs and `ContinuousOutput`, but not on the categoricals or any engineered feature — hoisting to `Feature` would add it to nine classes that lack it |
| `objective` | on both outputs and nowhere else, but required `AnyCategoricalObjective` vs `Optional[AnyObjective]` |
| `descriptors` | narrowed to `None` on both task inputs on purpose; the descriptions now say *why* it is disabled rather than restating the type |
| `features` | `ProductFeature` widens it (plain `List[str]`, dropping the uniqueness validator in `FeatureKeys` so `['x', 'x']` gives a quadratic term) while `CloneFeature` narrows it to `OneFeatureKeys` |

## Three docstring defects fixed rather than harvested

- **`CloneFeature`'s `Args:` block was copy-pasted from `ProductFeature`** — it said the features are "used to compute the product" and that repeating one is allowed. Neither is true: `CloneFeature` copies them, and its `OneFeatureKeys` type forbids duplicates. Harvesting mechanically would have published that into the schema.
- **`Output` documented `key`**, which `Feature` declares.
- **`SumFeature` and `MeanFeature` documented only inherited fields** (`features`, `keep_features`).

## Rename candidates

As agreed, collected rather than acted on — fields whose description exists mainly because the name does not carry it:

- **`DiscreteInput.rtol`** — relative tolerance for matching a provided value against `values`. The name says "some tolerance"; nothing indicates what it is compared against.
- **`ContinuousInput.allow_zero`** — makes the feature semi-continuous. The name reads like a validation flag rather than a statement about the feature's domain; `semicontinuous` would carry it.
- **`InterpolateFeature.normalize_y`** — a *divisor*, not a boolean, while its neighbour `normalize_x` is a boolean. The asymmetry is invisible from the names.

All three are breaking schema changes, so nothing was renamed here.

## Verification

- `pytest tests/bofire/data_models` — 1856 passed, 4 skipped
- `pytest tests/bofire -k "feature or input or output"` — 668 passed, 5 skipped
- ruff 0.6.5 clean; `ty==0.0.16` at 151 diagnostics, unchanged from main
- Confirmed `Feature.key` and `Feature.context` reach subclass schemas by inheritance, e.g. via `ContinuousInput.model_json_schema()`
- No `Attributes:` or `Args:` field blocks left in the package

No CHANGELOG entry: #802 announced the migration.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `529e3377f218`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.