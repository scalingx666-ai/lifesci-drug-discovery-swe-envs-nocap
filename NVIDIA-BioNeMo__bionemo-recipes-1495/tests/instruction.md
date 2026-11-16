# Issue

**Title:** fix: add get_seq_length to HFInferenceParams and relax ESM2 loss tolerance

## Description

## Summary

Fixes nightly CI failures in `unit-tests-recipes.yml` ([failed run](https://github.com/NVIDIA/bionemo-framework/actions/runs/22710936133)):

- **models/llama3** and **models/mixtral**: All `test_generate_with_cache*` tests failed with `AttributeError: 'HFInferenceParams' object has no attribute 'get_seq_length'`. HuggingFace transformers now calls `cache.get_seq_length()` during generation prefill. Added the method to `HFInferenceParams` in both models (and the llama3 recipe copy), returning the max cached sequence length from TE's `InferenceParams.sequences` dict.
- **models/esm2**: `test_golden_values` failed due to loss mismatch (expected 2.390625 vs 2.375, diff=0.015625) exceeding the `atol=1e-2` tolerance. Relaxed to `atol=2e-2`/`rtol=1e-2` to accommodate numerical differences in the updated container environment.

## Test plan

- [ ] CI `unit-tests-recipes` workflow passes for `models/esm2`, `models/llama3`, and `models/mixtral`
- [ ] Verify `test_generate_with_cache`, `test_generate_with_cache_batched`, and `test_generate_with_cache_beam_search` pass for llama3 and mixtral
- [ ] Verify `test_golden_values` passes for esm2

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c157a41ff8b2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.