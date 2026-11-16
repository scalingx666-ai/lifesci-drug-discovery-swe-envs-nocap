# Issue

**Title:** Fix cryptic error on duplicate register_* calls

## Description

## Problem

Every `register_*` function guarded against duplicates with an **identity** check (`if cls in registry: return`). Re-running registration code — e.g. re-executing a notebook cell — redefines the data model as a *new* class object that keeps the same `type` discriminator string. The identity guard missed it, the duplicate was appended, and the failure surfaced **later and cryptically** when Pydantic next built a dependent discriminated union:

```
TypeError: Value 'CustomStrategy' for discriminator 'type' mapped to multiple choices
```

This was reported for strategies but affected all registerables.

## Fix

Registration is now **discriminator-aware** across all registerables (strategies, kernels, priors/prior-constraints, engineered features, LLM providers, botorch surrogates). Both remedies are provided:

- **Default:** raise a clear, actionable `ValueError` on a same-`type`/different-class collision — it names the existing class, explains the notebook-rerun cause, and points to `overwrite=True`.
- **Opt-in `overwrite=True`:** cleanly replace the prior registration everywhere — registry lists, inline unions (which now self-heal), kernel sub-category lists, and functional-mapper dicts.
- Re-registering the **same** class object stays a silent no-op (unchanged behaviour).

Collision logic is centralized in `bofire/data_models/_register_utils.py` (`register_into`, `swap_or_append`, `pop_conflicting_map_keys`, and a discriminator-aware `append_to_union_field`) and threaded through every data-model and mapper `register` function via an `overwrite` flag. Mapper wrappers now validate via the data-model register **before** mutating maps, so a conflict never leaves partial state.

## Tests

Added duplicate-registration tests for each registerable (clear-error, `overwrite=True` rebuilds, same-class no-op, stale-map-key cleanup, inline-union self-heal).

- `tests/bofire/test_register.py`: 37 existing + 13 new — all pass
- Full data-model suite: 1412 passed, 5 skipped
- `ruff check` / `ruff format` clean; `ty check bofire` shows **147 diagnostics = identical to baseline** (zero introduced)

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1d760c048e9f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.