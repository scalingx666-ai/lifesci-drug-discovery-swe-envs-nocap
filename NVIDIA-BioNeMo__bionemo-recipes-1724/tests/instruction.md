# Issue

**Title:** fix(ci): keep llama3 on transformers 5.x (exclude 5.16 windowing regression) and make inv_freq non-persistent

## Description

## Summary

Keeps the llama3 environments on **transformers 5.x** (latest good 5.15.x) rather than downgrading to 4.x, and makes the llama3 model's rotary `inv_freq` buffer non-persistent so all `models/llama3` CI passes.

## Why / root cause

Two separate issues broke the llama3 nightly lanes:

1. **Tokenizer windowing regression (transformers 5.16.x only).** The unpinned `transformers` constraint resolved to 5.16.x, which regressed the fast tokenizer's `return_overflowing_tokens` windowing: with `max_length` + `stride` it returned only the final overflow window instead of all overlapping windows. Verified: transformers 5.0.0–5.15.x produce correct windows (e.g. 47 for 10kbp/1000/800); **5.16.0+ return 2**. The llama3 training dataset (`dataset.py`) relies on this for windowed training data, so it's a real production regression, not just a test artifact.
   - Fix: pin `transformers>=5.0.0,<5.16` (resolves to 5.15.1) — stay on transformers 5, avoid the one broken release line.

2. **Rotary `inv_freq` buffer persistence.** Transformer Engine registers `inv_freq` as a persistent buffer, but under transformers 5's meta-device checkpoint loading it is re-registered as non-persistent, so `test_rotary_inv_freq_after_from_pretrained` (added in #1715) asserted non-persistence. On transformers 4 it stayed persistent and the test failed.
   - Fix: re-register `inv_freq` as a **non-persistent** buffer in `NVLlamaModel` so persistence is consistent across transformers versions and the deterministic value is recomputed from config instead of round-tripped through the checkpoint.

## Changes

- `models/llama3/requirements.txt`, `recipes/llama3_native_te/requirements.txt`: `transformers>=5.0.0,<5.16`
- `models/llama3/modeling_llama_te.py` (and copied files `recipes/llama3_native_te`, `recipes/opengenome2_llama_native_te`): register `inv_freq` non-persistent, propagated via `ci/scripts/check_copied_files.py --fix`

## Validation (in CI container, pytorch26.04)

- transformers resolved to 5.15.1
- Tokenizer windowing: 10kbp→47 windows, production (8192/200)→7 windows ✅
- All assertions of `test_rotary_inv_freq_after_from_pretrained` pass (non-persistent buffer, correct device/dtype/value, `tie_weights` preserves customization) ✅
- `check_copied_files.py` and pre-commit pass ✅

Supersedes/ (which pinned `transformers<5`).

## Upstream tracking

- : open report for the `Encoding.overflowing` regression introduced in tokenizers 0.23.1
- : proposed upstream fix with truncation and stride regression tests
- : adoption of tokenizers 0.23.1, including the changed overflow expectation

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e3efd35e177a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.