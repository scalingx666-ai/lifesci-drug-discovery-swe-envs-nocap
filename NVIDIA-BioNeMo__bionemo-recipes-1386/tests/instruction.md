# Issue

**Title:** Add gradient accumulation to Llama3 recipe

## Description

### Description

Implements gradient accumulation for the Llama3 Native TE recipe, following the pattern from ESM2 PR #1254.

This enables training with larger effective batch sizes without increasing GPU memory usage by accumulating gradients across multiple microbatches before performing an optimizer step.

**Key Changes:**
- **perf_logger.py**: Added `log_micro_step()` method to track metrics across microbatches, updated `log_step()` signature to use accumulated metrics, added configurable `pad_token_id` parameter (defaults to 1)
- **train_ddp.py**: Implemented gradient accumulation loop with `model.no_sync()` for efficiency, added validation for `grad_acc_steps >= 1`
- **train_fsdp2.py**: Implemented gradient accumulation loop (without `model.no_sync()` as FSDP2 handles synchronization internally), added validation
- **defaults.yaml**: Added `grad_acc_steps` parameter (default: 1 for backward compatibility)
- **test_gradient_accumulation.py**: Added golden value test that validates mathematical correctness of gradient accumulation

**Validation:**
Lingua1B DCLM Benchmark trained with Grad_Acc=4, 2 Nodes, MBS=4 -> GBS=256 https://api.wandb.ai/links/clara-discovery/5laqf4gm
Has matching loss curve: 
<img width="3268" height="1454" alt="image" src="https://github.com/user-attachments/assets/55e5505f-5527-4a11-9a0d-9958eea046f0" />




DDP Results: https://api.wandb.ai/links/clara-discovery/6ncxn9n4
- DDP Training Loss curves for single node & 4 node training runs are similar with varying levels of gradient accumulation (grad acc=1, grad acc=2, grad acc=4) for a mbs=4: 
<img width="1260" height="641" alt="image" src="https://github.com/user-attachments/assets/02e610a7-704a-469b-97c0-fd6615c35cea" />

FSDP2 Results: https://api.wandb.ai/links/clara-discovery/lcvrsgm8

- FSDP2 Training Loss Curves for single node and 4 node training runs are similar with and without gradient accumulation: 
<img width="1265" height="627" alt="image" src="https://github.com/user-attachments/assets/0576bb6f-de0b-47b6-b305-9437366dd451" />



Golden value test confirms that `micro_batch=1, grad_acc=2` produces mathematically identical gradients to `micro_batch=2, grad_acc=1`.

**References:**
Adapts the gradient accumulation implementation from ESM2: #1254

#### Usage

##### Without gradient accumulation (default, backward compatible)
python train_fsdp2.py --config-name L2_lingua_1b

##### With gradient accumulation (reduce memory usage)
python train_fsdp2.py \
    --config-name L2_lingua_1b \
    dataset.micro_batch_size=2 \
    grad_acc_steps=2

##### Effective batch size formula:
effective_batch = micro_batch_size × num_gpus × grad_acc_steps
##### Example: 2 × 16 × 2 = 64 samples per optimizer step**Benefits:**
- Enables larger effective batch sizes on memory-constrained GPUs
- Allows training larger models by reducing micro batch size
- Maintains identical training dynamics to larger microbatches
- Backward compatible: `grad_acc_steps=1` behaves as before

#### Type of changes

- [x] New feature (non-breaking change which adds functionality)

### CI Pipeline Configuration

- [ciflow:all-recipes](https://github.com/NVIDIA/bionemo-framework/blob/main/docs/docs/main/contributing/contributing.md#ciflow:all-recipes) - Run tests for all recipes to validate gradient accumulation doesn't break existing tests

### Pre-submit Checklist

- [x] I have tested these changes locally (single-GPU validation on SLURM)
- [x] I have updated the documentation accordingly (inline comments, test docstrings)
- [x] I have added/updated tests as needed (test_gradient_accumulation.py with golden value test)
- [x] All existing tests pass successfully (pre-commit hooks pass, golden value test passes)

### Testing Notes

**Golden Value Test:**
pytest bionemo-recipes/recipes/llama3_native_te/tests/test_gradient_accumulation.py -vValidates that gradient accumulation produces mathematically equivalent gradients by comparing:
- Loss values (within 1% tolerance)
- Gradient norms (within 1% tolerance)  
- Individual parameter gradients (within 0.1% tolerance)

**Integration Testing:**
Testing with Lingua-1B benchmark on DCLM dataset - loss curves match

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `48739147692e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.