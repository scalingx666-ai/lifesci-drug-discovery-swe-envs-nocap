# Issue

**Title:** Refactor autoregressive model tests

## Description

Moves shared auto-regressive model tests to modeling_common, making it easier to add new auto-regressive models

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->
## Summary by CodeRabbit

* **Tests**
  * Added generation tests with KV-cache support across model architectures (ESM2, LLaMA3, Mixtral), including batched and beam search variants.
  * Expanded test infrastructure to support flexible configuration overrides in quantized model tests.

* **Bug Fixes**
  * Improved numerical stability in Mixtral by adjusting tensor dtype handling for expert routing operations.

* **Refactor**
  * Consolidated generation test implementations across models into shared base test class to reduce duplication.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bd72d882bca4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.