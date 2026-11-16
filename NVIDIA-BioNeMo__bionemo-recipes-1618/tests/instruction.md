# Issue

**Title:** evo2_megatron: SAE-recipe base Predict empty-batch fix, shared layer-truncation helper

## Description

Two small, self-contained additions to `evo2_megatron`.

### What's here
1. **predict empty-batch fix** — skip empty batches on a DP shard boundary.
2. **`load_model_to_layer` helper** (`run/predict.py`) — a reusable model loader:
   - `full=False`: truncate to `layer` with `post_process=False` → hidden states at that layer (for activation extraction / SAE encoding).
   - `full=True`: keep all layers + the LM head (logits) for generation.

### Why
`predict.py` already reads hidden states at a chosen layer via the `--embedding-layer` CLI path; this exposes that same truncated-load as a small reusable function, so tooling can load Evo2 to a layer programmatically instead of re-deriving the model-provider / precision / distributed setup each time.

### Tests
- CPU: `layer` is required when `full=False` (fails fast, no checkpoint I/O).
- GPU (`@pytest.mark.slow`): truncated load returns a usable `(model, tokenizer)`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `534f7f1a5e39`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.