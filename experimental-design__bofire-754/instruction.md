# Issue

**Title:** Fix MultiTaskGP serialization broken by new botorch default task prior

## Description

## Summary

`tests/bofire/surrogates/test_multitask_gps.py` currently fails against the botorch development branch (all 5 parametrizations of `test_MultiTaskGPModel`) at `model.dumps()` with:

```
AttributeError: Can't get local object 'PositiveIndexKernel.__init__.<locals>.<lambda>'
```

## Root cause (upstream)

Two recent botorch PRs combine to break `torch.save` on a default `MultiTaskGP`:

1.  (2026-04-09) — *Add setting_closure to PositiveIndexKernel for prior support*. Registers the task-correlation prior with two **inline lambdas** inside `PositiveIndexKernel.__init__`:
   ```python
   self.register_prior("IndexKernelPrior", task_prior,
                       lambda m: m._lower_triangle_corr,
                       lambda m, v: m._set_lower_triangle_corr(v))
   ```
2.  (2026-04-10) — *Add default BetaPrior(2.5, 1.5) for MultiTaskGP task covariance*. Changes the `MultiTaskGP` signature from `task_covar_prior: Prior | None = None` to `task_covar_prior: Prior | _DefaultType | None = DEFAULT`, which resolves to `BetaPrior(2.5, 1.5)`.

Before #3271, bofire never supplied a `task_covar_prior`, so the `if task_prior is not None` guard in `PositiveIndexKernel.__init__` kept the lambdas unregistered → the model was picklable. After #3271, the default `BetaPrior` is always registered → two module-scoped lambdas → `torch.save` fails because locally-defined lambdas are not picklable.

Version matrix:

| botorch version | Uses `PositiveIndexKernel`? | default `task_covar_prior` | lambda registered? | `dumps()` works? |
|---|---|---|---|---|
| ≤ v0.16.x | yes (#3047, v0.16.0) | `None` | no | ✅ |
| v0.17.0 – v0.17.2 (latest released) | yes | `None` | no | ✅ |
| botorch main / v0.17.3.dev | yes | `DEFAULT` → `BetaPrior(2.5, 1.5)` | **yes** | ❌ |

## Fix

One-line change in `bofire/surrogates/multi_task_gp.py`: pass `task_covar_prior=None` explicitly to `botorch.models.MultiTaskGP(...)`. This:

- works identically across all botorch versions (the keyword has existed for a long time and `None` was the prior default),
- short-circuits the lambda-based prior registration in `PositiveIndexKernel`, and
- preserves bofire's previous behavior (bofire never used the task covariance prior — the only supported `task_prior` in `MultiTaskGPSurrogate` is `LKJPrior`, and that path is already disabled with a warning).

## Follow-ups (out of scope for this PR)

- File a botorch issue asking for the lambdas in `PositiveIndexKernel.__init__` to be replaced with named methods so that default-constructed `MultiTaskGP` instances are again picklable.
- Once upstream is fixed, consider exposing the new `BetaPrior` default through `MultiTaskGPSurrogate` (would require widening `task_prior` beyond `LKJPrior`).

## Test plan

- [x] `pytest tests/bofire/surrogates/test_multitask_gps.py` — all 8 tests pass (previously 5 failed)
- [x] `pytest tests/bofire/strategies/test_multitask.py` — all 3 tests pass

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4f72eabc5048`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.