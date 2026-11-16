# Issue

**Title:** fix: stop torch and xgboost colliding over nvidia-nccl on Linux

## Description

`torch>=2.11` depends on `nvidia-nccl-cu13`; `xgboost` (`smact[ml]`) depends on `nvidia-nccl-cu12`. Both packages install to `nvidia/nccl/lib/libnccl.so.2` on Linux, so whichever installs last wins, leaving torch loaded against a mismatched NCCL ABI (`undefined symbol: ncclCommResume`). This is the exact collision described in #651, previously hidden by `pytest.importorskip`; #651's fix made it loud instead of silent, which is why `test (3.11/3.12, ubuntu-latest)` has been failing on `master` since it merged.

## Why not bump xgboost onto cu13 instead

Checked first — it's a dead end. xgboost drops Python 3.11 support at 3.3.0, *before* its own cu13 switch at 3.4.0. There's no xgboost release that supports Python 3.11 and depends on cu13, and SMACT still supports 3.11.

## Fix

Cap `torch` at `<2.11` — the last release still on the `nvidia-nccl-cu12` line, matching xgboost. Verified with `uv lock` across Python 3.11/3.12/3.13: both packages now resolve to the same `nvidia-nccl-cu12==2.27.5`, no `cu13` anywhere in the lockfile. `aviary-models` (the other `property_prediction` dependency, needs `torch>=2.3.0`) is still satisfied by the resulting `torch==2.10.0`.

This is a real `pyproject.toml` constraint, not a uv-only index trick, so it also fixes a plain `pip install smact[optional,property_prediction]` from PyPI — the scenario that originally surfaced this in #651.

## Caveat

This pins torch below its latest release for as long as xgboost stays on cu12. It's a coincidental-alignment fix, not a structural one — worth revisiting if either project's CUDA-generation support shifts again, or once SMACT can drop Python 3.11.

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->

## Summary by CodeRabbit

* **Bug Fixes**
  * Improved compatibility for property prediction installations on Linux by preventing conflicting NVIDIA communication libraries from being installed together.
  * Limited supported PyTorch versions to below 2.11 for this optional feature.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `97336357f0bf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.