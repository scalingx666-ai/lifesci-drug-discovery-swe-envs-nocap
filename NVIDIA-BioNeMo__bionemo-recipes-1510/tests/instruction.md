# Issue

**Title:** Add expert parallelism support to mixtral

## Description

- Adds DTensor-based expert parallelism (EP) to the Mixtral MoE model, enabling experts to be sharded across GPUs using PyTorch's DTensor with Shard(0) placement on  the expert dimension                                                       
- Introduces two pluggable TokenDispatcher implementations behind a common protocol:
  - AllToAllTokenDispatcher (default) — uses NCCL all_to_all_single to exchange tokens between EP ranks, with TE moe_permute/moe_unpermute for local expert sorting. Works everywhere NCCL is available.
  - FusedTokenRouter — uses https://github.com/deepseek-ai/DeepEP fused all-to-all kernels (fused_dispatch/fused_combine) with a Triton index-conversion kernel, providing a higher-performance alternative when deep_ep is installed
- Either dispatcher can be injected into NVMixtralForCausalLM via the dispatcher= constructor argument; the model is otherwise agnostic to the communication backend
- EP is activated by calling model.model.set_ep_groups(ep_group, ep_mesh), which wraps expert weight tensors as DTensors and configures the active dispatcher

All tests are multi-GPU and launch via torchrun subprocesses:

- test_ep.py — Numerical equivalence: EP=2 produces the same logits and loss as EP=1 on identical weights and inputs
- test_ep_dcp.py — DCP round-trip: save an EP=2 model with torch.distributed.checkpoint, reload into a fresh model, verify exact weight and logit match. Also tests save_final_model_ep which gathers sharded experts into a single safetensors file loadable by an EP=1 model
- test_fsdp_ep.py — FSDP2 + EP composition: verifies training (forward + backward + optimizer step) works for FSDP=2/EP=1 (2 GPUs), FSDP=1/EP=2 (2 GPUs), and FSDP=2/EP=2 (4 GPUs) on a 2D (dp, ep) device mesh
- test_hybrid_ep.py — FusedTokenRouter equivalence: verifies that forward logits/loss and backward gradients match the AllToAllTokenDispatcher reference (requires deep_ep + NVLink peer access)

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->

## Summary by CodeRabbit

## Release Notes

* **New Features**
  * Added Expert Parallelism (EP) support for distributed MoE training with device mesh sharding.
  * Introduced optimized fused dispatch/combine mechanism for improved token routing efficiency.
  * Added support for distributed checkpointing and final model gathering with simplified weight handling.

* **Documentation**
  * Enhanced README with comprehensive Expert Parallelism setup and configuration guidance.

* **Chores**
  * Added automated installation script for DeepEP hybrid expert parallelism backend.
  * Expanded test coverage for distributed training scenarios including FSDP2 and checkpoint operations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0553cab88485`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.