# Issue

**Title:** fix: force float32 precision on CPU to prevent distorted structures

## Description

This updates PR #670 from the blanket CPU float32 workaround in `main.py`
to the underlying fix described in #662.

On CPU, PyTorch Lightning wraps the forward pass with
`torch.autocast("cpu", dtype=torch.bfloat16)`, so
`torch.autocast("cuda", enabled=False)` is a no-op there. As a result,
the structure and affinity blocks in `boltz2.py` still run under CPU bf16
autocast even though they explicitly cast inputs to float32.

This patch:
- removes the `main.py` CPU precision workaround from this PR
- adds an `autocast_device_type()` helper in `model/modules/utils.py`
- replaces the three hardcoded `torch.autocast("cuda", enabled=False)`
  blocks in `src/boltz/model/models/boltz2.py` with
  `torch.autocast(autocast_device_type(s.device.type), enabled=False)`

Local validation:
- under `torch.autocast("cpu", dtype=torch.bfloat16)`, the old path keeps
  matmul in `torch.bfloat16`
- the new `autocast_device_type(...)` path correctly yields `torch.float32`

Credit:
- @Christopher-Lee-McClendon for the root-cause diagnosis in #662
- @volgin for the helper-based fix pattern used in boltz-community
- @ozvoz for validating the earlier workaround in #653

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cb04aeccdd48`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.