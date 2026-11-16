# Issue

**Title:** Migrate ESM models to AttentionMaskConverter (replace deprecated get_extended_attention_mask)

## Description

### Description

Replaces the local `NVEsmPreTrainedModel.get_extended_attention_mask` added in #1746 (a re-implementation of the deprecated `ModuleUtilsMixin` method) with `transformers.modeling_attn_mask_utils.AttentionMaskConverter`.

In `NVEsmModel.forward`:

```python
- extended_attention_mask = self.get_extended_attention_mask(attention_mask, input_shape)
+ extended_attention_mask = AttentionMaskConverter(is_causal=False).to_4d(
+     attention_mask, query_length=1, dtype=self.dtype
+ )
  extended_attention_mask = extended_attention_mask < -1  # TE boolean mask, True = masked
```

`to_4d` with `query_length=1` yields the same `[batch, 1, 1, seq_len]` additive mask (0 / `dtype.min`) the old helper produced, so the boolean mask handed to TE's `padding` attention is unchanged in shape and values. The removed helper's 3D/4D mask branches were dead code: `NVEsmEmbeddings` already assumes a 2D `[batch, seq_len]` mask (`attention_mask.unsqueeze(-1)`).

The four recipe copies were regenerated with `python ci/scripts/check_copied_files.py --fix`:
- `recipes/esm2_native_te/modeling_esm_te.py`
- `recipes/esm2_peft_te/example_8m_checkpoint/esm_nv.py`
- `recipes/esm2_accelerate_te/example_8m_checkpoint/esm_nv.py`
- `recipes/vllm_inference/esm2/modeling_esm_te.py`

#### Usage

No user-facing change; `NVEsmModel(...)(input_ids, attention_mask)` behaves as before.

### Type of changes

- [ ] Bug fix (non-breaking change which fixes an issue)
- [ ] New feature (non-breaking change which adds functionality)
- [x] Refactor
- [ ] Documentation update
- [ ] Other (please describe):

### CI Pipeline Configuration

Configure CI behavior by applying the relevant labels. By default, only basic unit tests are run.

- [ciflow:skip](https://github.com/NVIDIA/bionemo-framework/blob/main/docs/docs/main/contributing/contributing.md#ciflow:skip) - Skip all CI tests for this PR
- [ciflow:notebooks](https://github.com/NVIDIA/bionemo-framework/blob/main/docs/docs/main/contributing/contributing.md#ciflow:notebooks) - Run Jupyter notebooks execution tests
- [ciflow:slow](https://github.com/NVIDIA/bionemo-framework/blob/main/docs/docs/main/contributing/contributing.md#ciflow:slow) - Run slow single GPU integration tests marked as @pytest.mark.slow
- [ciflow:all](https://github.com/NVIDIA/bionemo-framework/blob/main/docs/docs/main/contributing/contributing.md#ciflow:all) - Run all tests, including unit tests, slow tests, notebooks, and every recipe/model directory.

### Pre-submit Checklist

- [ ] I have tested these changes locally — not possible: `transformers`/`transformer_engine` are not installable in the (network-restricted) authoring environment and the tests require a GPU. Verified `python ci/scripts/check_copied_files.py` passes and the module compiles. Relying on CI for `models/esm2` and the ESM2 recipe unit tests.
- [x] I have updated the documentation accordingly (n/a)
- [x] I have added/updated tests as needed (existing ESM2 forward-pass tests cover this)
- [ ] All existing tests pass successfully (pending CI)

Link to Devin session: https://nvidia-cloud.devinenterprise.com/sessions/203edf71bd464abc9fd15feaf9218a9c
Open in Devin Desktop: https://nvidia-cloud.devinenterprise.com/desktop/session/203edf71bd464abc9fd15feaf9218a9c?variant=devin

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->

## Summary by CodeRabbit

* **Bug Fixes**
  * Improved attention-mask handling across ESM2 model variants and inference recipes.
  * Padding masks are now converted consistently for Transformer Engine, improving compatibility and mask correctness.

* **Refactor**
  * Replaced custom attention-mask conversion logic with the standard Transformers implementation.
  * Removed the previously exposed custom attention-mask helper method.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1b30b70465b3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.