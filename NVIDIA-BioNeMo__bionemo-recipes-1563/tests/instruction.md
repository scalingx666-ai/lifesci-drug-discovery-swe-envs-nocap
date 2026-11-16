# Issue

**Title:** fix: relax BF16 logits tolerance in stop-and-go test and xfail AMPLIFY FSDP2 test

## Description

## Nightly CI Fix (2026-04-25)

Fixes two nightly CI failures in `unit-tests-recipes.yml` ([run](https://github.com/NVIDIA/bionemo-framework/actions/runs/24927691604)):

### 1. `esm2_native_te` — `test_stop_and_go.py`
**Root cause:** BF16 numerical tolerance too tight. The logits comparison used `atol=1.5e-2` but observed max diff was `0.017334` after 10 training steps with BF16 precision.

**Fix:** Relaxed `atol` from `1.5e-2` to `2.0e-2` with updated comment.

### 2. `esm2_accelerate_te` — `test_accelerate_amplify.py`
**Root cause:** The AMPLIFY model (from HuggingFace Hub) does not implement `get_input_embeddings()`, which the newer `accelerate` FSDP2 API now requires during model preparation.

**Fix:** Marked `test_te_with_fsdp2_config` as `xfail(strict=True)` — this is an upstream compatibility issue between the AMPLIFY model and accelerate.

---
*Automated fix by svc-bionemo nightly CI monitor.*

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1263f64629ec`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.