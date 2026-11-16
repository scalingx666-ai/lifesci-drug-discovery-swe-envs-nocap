# Issue

**Title:** fix(mixtral,qwen): accept missing attention mask on THD packing path (transformers 5.18)

## Description

### Description

Fixes the 2026-09-30 nightly failure of `unit-tests (models/mixtral)` and `unit-tests (models/qwen)` (https://github.com/NVIDIA-BioNeMo/bionemo-recipes/actions/runs/36695045184). The failing tests are `test_generate_with_cache*`, and they fail with `AssertionError: Attention mask is required when packing BSHD inputs.`

**Root cause (upstream):** transformers 5.18.0 was released on 2026-09-30 at 16:45 UTC. Its `generate()` now drops all-ones attention masks:
```python
if not is_encoder_decoder and accepts_attention_mask and (attention_mask == 1).all():
    model_kwargs["attention_mask"] = None
```
`models/mixtral` and `models/qwen` don't pin transformers, so the nightly picked up 5.18.0. `models/llama3` pins `<5.16` and isn't affected. The same SHA passed every nightly from 09-19 through 09-29.

**Fix:** on the BSHD->THD packing path, a missing mask now means no padding:
```diff
 if should_pack_inputs:
-    assert attention_mask is not None, "Attention mask is required when packing BSHD inputs."
+    if attention_mask is None:
+        attention_mask = torch.ones(hidden_states.shape[:2], dtype=torch.long, device=hidden_states.device)
```
This gives the same behavior as before in both cases:
- **Prefill:** an all-ones `[B, L]` mask.
- **Decode:** a `[B, 1]` mask, which produces the same `cu_seqlens` and `InferenceParams` lengths (`[1]*B`) as the old path.

Changed files:
- `models/mixtral/modeling_mixtral_te.py`, synced to `recipes/mixtral_native_te/modeling_mixtral_te.py` with `check_copied_files.py --fix`
- `models/qwen/modeling_qwen2_te.py` and `models/qwen/modeling_qwen3_te.py`
- `models/mixtral/tests/test_modeling_mixtral.py`: a new test checks that a THD forward pass with no mask matches one with an all-ones mask.

Note: I committed with `SKIP=gitleaks` (Peter approved this). The sandbox can't install the Go toolchain that the hook needs. All other hooks ran and passed. The CI pre-commit job still runs gitleaks.

#### Usage

```python
model(input_ids=input_ids)  # attn_input_format="thd", no attention_mask -> treated as unpadded
```

### Type of changes

- [x] Bug fix (non-breaking change which fixes an issue)
- [ ] New feature (non-breaking change which adds functionality)
- [ ] Refactor
- [ ] Documentation update
- [ ] Other (please describe):

### Pre-submit Checklist

- [ ] I have tested these changes locally (no GPU in the sandbox; ruff, license and copied-files checks pass, so this relies on CI)
- [ ] I have updated the documentation accordingly
- [x] I have added/updated tests as needed
- [ ] All existing tests pass successfully

Link to Devin session: https://nvidia-cloud.devinenterprise.com/sessions/44900e0b1d7d45e397bb1bb8ffd7c48d
Open in Devin Desktop: https://nvidia-cloud.devinenterprise.com/desktop/session/44900e0b1d7d45e397bb1bb8ffd7c48d?variant=devin
<!-- devin-review-badge-begin -->

---

<a href="https://nvidia-cloud.devinenterprise.com/review/nvidia-bionemo/bionemo-recipes/pull/1766" target="_blank"><picture><source media="(prefers-color-scheme: dark)" srcset="https://static.devin.ai/assets/gh-devin-review-dark.svg?v=4"><img src="https://static.devin.ai/assets/gh-devin-review-light.svg?v=4" alt="Devin Review"></picture></a>
<!-- devin-review-badge-end -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `11701476b005`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.