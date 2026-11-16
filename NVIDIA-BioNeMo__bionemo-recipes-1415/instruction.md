# Issue

**Title:** Add tensor parallelism to the cp-aware dataloader and collator

## Description

Handles the case of replicating the input data across TP ranks with the CP aware dataloader

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->

## Summary by CodeRabbit

* **New Features**
  * Added tensor-parallel support to context-parallel data loading across model implementations, enabling efficient batch replication and distributed rank handling

* **Tests**
  * Introduced comprehensive distributed testing suite covering multiple data loading scenarios and configurations

* **Chores**
  * Updated test configuration references for deterministic model checkpoints

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `79ca3bd8ef96`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.