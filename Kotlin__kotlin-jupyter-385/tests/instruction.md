# Issue

**Title:** Support display id in `display(value)` API.

## Description

* Add nullable `id` argument to `ScriptTemplateWithDisplayHelpers.DISPLAY` and `KotlinKernelHost.display` methods in kernel API.
* Add `overrideId` argument to `DisplayResult.toJson` method

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fdd512b71893`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.