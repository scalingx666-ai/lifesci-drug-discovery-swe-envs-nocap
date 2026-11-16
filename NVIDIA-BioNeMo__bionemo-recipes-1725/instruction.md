# Issue

**Title:** fix(evo2): raise warp-lang floor to >=1.14 for subquadratic-ops-torch

## Description

## Summary

Fix the failing nightly Evo2 CI (`unit-tests-recipes.yml`) that broken at **pytest collection** for `recipes/evo2_megatron`, `recipes/evo2_phage_gen`, and the `evo2_megatron` notebook tests with:

```
ERROR tests/bionemo/evo2 - AttributeError: module 'warp' has no attribute 'LOG_WARNING'
```

## Root cause

`subquadratic-ops-torch-cu13` is an **unpinned** dependency, so `uv` resolves the latest `0.3.0`. That version's `subquadratic_ops_torch/implicit_filter.py` runs, at module import:

```python
wp.config.log_level = wp.LOG_WARNING
```

I verified by installing every `warp-lang` release and checking the API:

| warp-lang | `wp.LOG_WARNING` / `wp.config.log_level` |
|---|---|
| 1.0.2 – 1.13.0 | ❌ absent |
| 1.14.0, 1.15.0, 1.16.0 | ✅ present |

The recipes' `.ci_build.sh` pinned `warp-lang<1.13.0` (a leftover guard for the stale `subquadratic-ops-torch` 0.2.0 that used `wp.context`), so warp resolved to 1.12.x, which **lacks** `LOG_WARNING`. That pin is what caused the collection failure — it is the opposite of what `subquadratic-ops-torch` 0.3.0 needs.

Note: I also checked the public PyPI 0.3.0 wheel directly — it does contain the `LOG_WARNING` line (it is not an internal-index-only build), and it uses `wp.Module` (not `wp.context.Module`), confirming it targets `warp-lang >= 1.13/1.14`.

## Fix

Raise the warp-lang floor from `<1.13.0` to **`warp-lang>=1.14,<1.17`** in:

- `recipes/evo2_megatron/.ci_build.sh`
- `recipes/evo2_megatron/Dockerfile`
- `recipes/evo2_phage_gen/.ci_build.sh`

The floor guarantees the `LOG_WARNING`/`config.log_level` symbols exist; the `[1.14, 1.17)` window covers the verified-working versions (1.14/1.15/1.16) and defensively caps against a not-yet-validated warp 1.17+.

## Validation

Ran the full CI install + `pytest -v .` for `recipes/evo2_megatron` inside the exact CI container (`svcbionemo023/bionemo-framework:pytorch26.04-py3-squashed`) with 2x RTX 5090:

- **Installation succeeds**, resolving `warp-lang` 1.16.0.
- **Collection passes** — the `LOG_WARNING` `AttributeError` is gone (was a hard collection error before the fix).
- `import subquadratic_ops_torch.implicit_filter` succeeds with warp 1.14.0 / 1.15.0 / 1.16.0, and fails with warp 1.12.1 (reproducing the exact CI error).
- Test result: `445 passed, 26 skipped, 1 xfailed, 1 xpassed`; subquadratic-ops prefill/cuda-graph tests (`test_infer_evo2_short_prefill_is_prefix_invariant... [subquadratic-ops]`, `test_subquadratic_ops_with_cuda_graph_matches_baseline[...]`) pass.

Remaining `6 failed + 3 errors` in the local run are unrelated to this change and are hardware/environment-specific on these 32 GB RTX 5090 consumer cards (7B-model CUDA OOM, Blackwell numerical-tolerance drift on a log-prob assert, 2-GPU distributed-training checkpoint equality, and a `torch.load(weights_only=True)` numpy-global allowlist error). CI runs on `linux-amd64-gpu-l4-latest-1` with different memory characteristics.

## Scope

Changes are confined to the two Evo2 recipes (`.ci_build.sh` and the megatron `Dockerfile`); no llama3 files touched, no copied-files mapping affected (`python ci/scripts/check_copied_files.py` passes).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e3efd35e177a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.