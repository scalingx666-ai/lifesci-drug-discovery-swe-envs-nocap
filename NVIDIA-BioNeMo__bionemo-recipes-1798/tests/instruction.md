# Issue

**Title:** fix(esm2): drop AttentionMaskConverter, forward-pass export smoke test, nightly Hub remote-code check

## Description

### Description

All six `nvidia/esm2_*` Hub repos serve the same out-of-date `esm_nv.py` (exported 2026-04 with transformers 5.5.0). Its `NVEsmModel.forward` calls `self.get_extended_attention_mask(...)`, which current transformers (5.20) no longer has. So the checkpoints load fine with `trust_remote_code=True` and then raise `AttributeError` on the first forward pass. #1748 fixed the repo's copy but the Hub was never re-exported. CI didn't catch it because L0 tests use the local `example_8m_checkpoint`, the `export.py` smoke test only loads the model, and nothing ran the Hub code.

This PR:

- **`models/esm2/modeling_esm_te.py`**: builds TE's boolean padding mask directly with `attention_mask[:, None, None, :] == 0`. This replaces `AttentionMaskConverter(is_causal=False).to_4d(...) < -1`, which is deprecated and emits a `FutureWarning` on every call in transformers 5.20.2. The result is the same: a `[batch, 1, 1, seq]` bool mask, `True` = masked. I checked it matches the old mask exactly for long/float/bool masks with bf16/fp32. The modeling code no longer uses any transformers mask helper, so a future transformers release can't break it the same way.
- **`models/esm2/export.py`**: the smoke test now runs a padded bf16 forward pass on GPU with the bundled `esm_nv.py` and checks the logits' shape and that they are finite. An export that loads but can't run now fails before upload.
- **`models/esm2/tests/test_export.py`**: new `test_exported_checkpoint_forward_pass` that does the same check against the exported 8M checkpoint.
- **`models/esm2/tests/test_hub_checkpoints.py`** (new): for every tag in `ESM_TAGS`, downloads only `config.json`, `esm_nv.py` and the tokenizer from `nvidia/<tag>`, with no weights. It builds a 2-layer random-init model via `AutoModelForMaskedLM.from_config(config, trust_remote_code=True)` and runs a padded forward + backward pass, about 3 s per repo. It is skipped unless `GITHUB_EVENT_NAME == "schedule"` (the nightly run) or `ESM2_TEST_HUB_CHECKPOINTS=1`. That way it alerts on the nightly without blocking PRs while the Hub is stale.
  - Validated in this PR's CI with a temporary commit that enabled it (since removed). All 6 Hub repos failed with `AttributeError: 'NVEsmModel' object has no attribute 'get_extended_attention_mask'`, which is the reported bug, and everything else in `models/esm2` passed. The nightly `unit-tests (models/esm2)` will stay red until the Hub is re-exported.
- Copies regenerated with `ci/scripts/check_copied_files.py --fix` (esm2_native_te, esm2_peft_te / esm2_accelerate_te `example_8m_checkpoint/esm_nv.py`, vllm_inference/esm2).

**Follow-up (needs nvidia HF org write access):** once this merges, re-run `export.py` and `hf upload` every `nvidia/esm2_*` repo (steps in `models/esm2/README.md`). The weights don't change.

#### Usage

```bash
# Run the Hub remote-code check locally (GPU required)
cd models/esm2 && ESM2_TEST_HUB_CHECKPOINTS=1 pytest -v tests/test_hub_checkpoints.py
```

### Type of changes

- [x] Bug fix (non-breaking change which fixes an issue)
- [ ] New feature (non-breaking change which adds functionality)
- [ ] Refactor
- [ ] Documentation update
- [ ] Other (please describe):

### Pre-submit Checklist

- [x] I have tested these changes locally (mask equivalence on CPU; GPU tests via PR CI)
- [ ] I have updated the documentation accordingly
- [x] I have added/updated tests as needed
- [x] All existing tests pass successfully

Link to Devin session: https://nvidia-cloud.devinenterprise.com/sessions/3ee68d4bee0b41aeb2ca125e1fbff489
Open in Devin Desktop: https://nvidia-cloud.devinenterprise.com/desktop/session/3ee68d4bee0b41aeb2ca125e1fbff489?variant=devin
Requested by: @pstjohn

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
  * Improved handling of padded sequences in ESM2 models, helping ensure padding is correctly excluded during processing.
* **Tests**
  * Exported checkpoints are now checked with sample inputs, including validation of output shapes and finite results.
  * Added coverage for Hub checkpoints, including checks for model outputs, training loss, and gradients.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `107d37305593`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.