# Issue

**Title:** ci: exclude vllm_inference and megatron from nightly recipe CI

## Description

## Problem

The 26.03 container update brought `transformers==5.5.4`, which breaks the vllm_inference recipe CI:

### vLLM 0.15.1 (current) + transformers 5.x
- vLLM 0.15.1 hard-requires `transformers < 5`
- `install_vllm.sh` installs vLLM (which pins transformers <5), then upgrades transformers back to 5.x
- This creates a broken environment — vLLM is installed against transformers 4.x but runs with 5.x
- Additionally, the `nvidia/esm2_*` Hub models have `"tokenizer_class": "TokenizersBackend"` in their `tokenizer_config.json`, a class that only exists in transformers 5.x. If vLLM downgrades to <5, tokenizer loading fails

### vLLM 0.19.1 (latest, supports transformers 5.x)
- Requires `transformers >= 5.5.1` ✅
- But uses `register_opaque_type(hoist=True)` in `vllm/utils/torch_utils.py`, gated behind `is_torch_equal_or_newer("2.11.0.dev")`
- The NGC 26.03 torch build (`2.11.0a0+nv26.03`) matches that version check, but does **not** have the upstream `hoist` parameter on `register_opaque_type` yet
- Result: `TypeError: register_opaque_type() got an unexpected keyword argument 'hoist'` at import time

### Megatron duplicates
- Megatron recipes (`eden_megatron`, `evo2_megatron`) already have a dedicated CI workflow (`unit-tests-mbridge-recipes.yaml`) but were also running as duplicates in this recipes workflow on nightly

## Fix

Exclude both `vllm_inference` and `megatron` from the `ALL_DIRS` nightly enumeration in `unit-tests-recipes.yml`:
- **vllm_inference**: blocked until either NGC ships torch with the upstream `hoist` API (enabling vLLM 0.19.1) or vLLM releases a version compatible with both the NGC torch build and transformers 5.x
- **megatron**: removes duplicate nightly runs (already covered by `unit-tests-mbridge-recipes.yaml`)

Both were already excluded from PR `changed-files` detection but scheduled runs bypass that filter.

## Related
- #1553 — Fixed `HFInferenceParams.is_compileable` for transformers 5.x (merged)
- #1555 — Fixes ESM2 tokenizer export to write `PreTrainedTokenizerFast` instead of `TokenizersBackend`

## Failing CI run
https://github.com/NVIDIA/bionemo-framework/actions/runs/24601629903

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `748ec4c677df`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.