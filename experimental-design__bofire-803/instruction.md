# Issue

**Title:** Document the objectives and priors data models

## Description

Second package batch of the migration started in #802. Drains the `objectives` and `priors` allowlists to zero — **49 field descriptions and one class docstring**, taking the ratchet from 551 to 501 remaining entries.

The two packages go together because they sit next to each other alphabetically in the allowlist; splitting them would have produced a merge conflict between the two PRs for no reviewer benefit.

## Mostly harvest, three judgment calls

41 of the 49 descriptions came from existing `Attributes:` blocks, which are now removed. The rest needed more than a move:

**`LKJPrior`'s docstring was stale.** It documented `n` and `eta`; the fields have been `n_tasks` and `shape` since the gpytorch mapping was written (`bofire/priors/mapper.py:83-87` maps `n_tasks`→`n`, `shape`→`eta`). The prose was recovered under the current names rather than discarded — worth a look to confirm I mapped them the way you'd expect.

**`DimensionalityScaledLogNormalPrior` had no prose anywhere.** Its semantics came from `mapper.py:97-107`, and the effective-parameter formula is now stated in the class docstring the same way its Gamma sibling already states its own:

```
loc_eff   = loc + log(d) * loc_scaling
scale_eff = sqrt(scale**2 + log(d) * scale_scaling)
```

**Several subclasses documented fields they don't declare** — `clip`, `w` and `bounds` throughout `desirabilities.py`, and all three interval fields in `NonTransformedInterval` / `LogTransformedInterval`. Per the rule established in #802 those entries were dropped, with one canonical description on the declaring class. Where a subclass genuinely *reinterprets* an inherited field, that goes in its class docstring instead: `MovingMaximizeSigmoidObjective` treats `tp` as a relative turning point, which the shared `SigmoidObjective.tp` description cannot say.

## Verification

- `pytest tests/bofire/data_models` — 1856 passed, 4 skipped
- `pytest tests/bofire -k "objective or prior or desirab"` — 382 passed, 32 skipped
- ruff 0.6.5 clean; `ty==0.0.16` at 151 diagnostics, unchanged from main
- Zero `objectives` / `priors` entries left in either allowlist

No CHANGELOG entry: #802 announced the migration, and a per-package entry would conflict on every subsequent PR.

As with #802, none of this is visible on the website yet — quartodoc drops pydantic fields until the rendering work lands. The payoff is in `model_json_schema()`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8fc239ae1daf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.