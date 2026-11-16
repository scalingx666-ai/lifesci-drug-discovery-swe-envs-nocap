# Issue

**Title:** quick fp8 cleanup

## Description

Moves the fp8 init to a separate fp8_debugging file, moves step call to the perf logger

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->

## Summary by CodeRabbit

* **New Features**
  * Added FP8 debugging and statistics tracking capabilities to ESM2 and Llama3 recipe models, with validation ensuring FP8 debugging is only enabled when FP8 autocast is active.
  * Enhanced performance logging to support FP8 statistics collection during training.

* **Refactor**
  * Refactored training scripts with modular FP8 debugging initialization, reducing inline setup complexity and improving code organization.

<sub>✏️ Tip: You can customize this high-level summary in your review settings.</sub>

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6704a71d9998`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.