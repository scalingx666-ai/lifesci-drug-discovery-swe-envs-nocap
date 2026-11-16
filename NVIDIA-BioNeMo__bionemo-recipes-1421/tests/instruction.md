# Issue

**Title:** Demonstrate dcp checkpoint save resume with context parallel

## Description

Makes it easier to run BSHD context parallel runs in the llama3 recipe for local testing, and adds checkpoint save/resume checks to the llama3 recipe

BIO-8

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->

## Summary by CodeRabbit

## Release Notes

* **New Features**
  * Added checkpoint save/restore capabilities and worker configuration querying for context-parallel data loading
  * Introduced new configuration parameter for sequence padding control

* **Improvements**
  * Enhanced distributed training support with improved checkpoint integration for context parallelism

* **Tests**
  * Added comprehensive integration tests for distributed checkpointing with context parallelism
  * Added multi-GPU training tests with different attention format configurations

<sub>✏️ Tip: You can customize this high-level summary in your review settings.</sub>

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e53b72650be3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.