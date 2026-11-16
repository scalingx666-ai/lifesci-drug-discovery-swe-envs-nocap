# Issue

**Title:** Fix HFInferenceParams missing is_compileable for transformers 5.x compatibility

## Description

## Problem

Nightly CI has been failing for 7 consecutive days (4/11–4/17) across `models/mixtral`, `models/llama3`, `models/qwen`, and `verify-recipe-tests`.

All failures share the same root cause:
```
AttributeError: 'HFInferenceParams' object has no attribute 'is_compileable'
```

The 26.03 PyTorch container update (#1540) brought `transformers==5.5.4`, which added an `is_compileable` property check on cache objects during `generate()`. The custom `HFInferenceParams` class does not implement this property.

## Fix

Added `is_compileable` property returning `False` to `HFInferenceParams` in all 6 affected files (4 model sources + 2 recipe copies). The property returns `False` since this custom TE-based cache wrapper is not compatible with `torch.compile`.

## Failing CI run
https://github.com/NVIDIA/bionemo-framework/actions/runs/24558420210

## Testing
- Pre-commit checks pass
- `check_copied_files.py` confirms all copies are in sync
- Fix is minimal and targeted (5 lines per file)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b508876dcd97`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.