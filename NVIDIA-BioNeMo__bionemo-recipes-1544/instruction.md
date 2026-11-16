# Issue

**Title:** Fix multi-GPU FSDP2 IndexError in mixtral_native_te recipes

## Description

### Description

Fixes and extends the mixtral_native_te recipes from #1543.

**Commit 1: Fix multi-GPU FSDP2 IndexError**

- `_sync_expert_views()` iterated `range(self.num_local_experts)` but after FSDP2 sharding, the local tensor has fewer experts → IndexError. Fixed to use actual tensor shape.
- `_restack_from_views()` now handles DTensor params by materializing the local shard on CUDA and reconstructing the DTensor wrapper via `setattr`.
- Bumped flaky bshd loss threshold from 8.0 → 8.5.

**Commit 2: Add FSDP2 + Expert Parallelism tests**

Adds EP tests for both `mixtral_native_te` and `opengenome2_mixtral_native_te` recipes:
- `test_fsdp2_ep1` — FSDP=2, EP=1 (2 GPUs): data-parallel sharding, all experts on each rank
- `test_fsdp1_ep2` — FSDP=1, EP=2 (2 GPUs): expert-parallel training with all-to-all communication

Each test creates a 2D device mesh, sets EP groups, wraps with FSDP2, runs one training step, and verifies finite loss/gradients and weight updates.

### Testing

All tests pass on 2× RTX 5090:
- ✅ `mixtral_native_te/tests/test_train.py` (4/4)
- ✅ `mixtral_native_te/tests/test_lingua_small_mixtral.py` (1/1)
- ✅ `mixtral_native_te/tests/test_train_two_gpu.py` (1/1)
- ✅ `mixtral_native_te/tests/test_fsdp_ep.py` (2/2)
- ✅ `opengenome2_mixtral_native_te/tests/test_train.py` (6/6)
- ✅ `opengenome2_mixtral_native_te/tests/test_dataset.py` (14/14)
- ✅ `opengenome2_mixtral_native_te/tests/test_train_two_gpu.py` (2/2)
- ✅ `opengenome2_mixtral_native_te/tests/test_fsdp_ep.py` (2/2)

### Type of changes

- [x] Bug fix (non-breaking change which fixes an issue)
- [x] New feature (non-breaking change which adds functionality)

Builds on #1543

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `47cddb376c0e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.