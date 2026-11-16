# Issue

**Title:** Fix Llama3 golden-value failures after checkpoint loading

## Description

## What changed

- Cherry-pick `9a496964b533` from #1714 without modification.
- Reinitialize Transformer Engine's non-persistent rotary `inv_freq` buffer after meta-device checkpoint loading.
- Add regression coverage for `from_pretrained()` and improve shared golden-value test cleanup/comparison behavior.
- Preserve the related shared-harness and Evo2 test compatibility updates from the original commit so Git can recognize the same changes when #1714 merges.

## Why

Scheduled CI run https://github.com/NVIDIA-BioNeMo/bionemo-recipes/actions/runs/31477466541 failed three `models/llama3` golden-value tests. The TE model was loaded with an uninitialized RoPE buffer, producing losses of 8.0031 and 4.1343 versus the Hugging Face reference value of 2.0217. The `verify-recipe-tests` failure was a downstream aggregate failure.

Reusing the existing #1714 commit fixes the regression while minimizing future merge conflicts.

## Validation

- `python ci/scripts/check_copied_files.py --fix`
- `pre-commit run --from-ref upstream/main --to-ref HEAD`
- Python bytecode compilation for the changed Python modules
- `git diff --check upstream/main...HEAD`

The focused Llama3 GPU regression test could not run in the local host environment because PyTorch is not installed; the repository's CI model container provides the required PyTorch, Transformer Engine, and GPU runtime.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5aae77874894`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.