# Issue

**Title:** MVP CI/CD Implementation for QUICK CUDA (with f functions) Build and Test Workflow

## Description

This workflow is for QUICK build and test CUDA version with f functions enabled.

This version can take a long time and thus may (at times) timeout/disconnect (ie. because of how long it takes, it can accidentally disonnect from server node). The time for build can vary / be unpredictable. The maximum timeout duration has been set to 48 hours to best ensure that the job can run to completion, however this does not guarantee it won't lose connection. The default build and test workflow should still be without f functions enabled, which should run automatically (#476 ) with this (enablef) workflow being ran only if needed.

Because of the memory demands of this workflow, the runner requests 48GB of memory. Since the workflow without f functions could pass with just 8GB of memory it may be optimal to have separate runners but for now we just have one runner  requesting 48GB of memory.

The workflow can only be triggered manually through the run workflow button.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `74ed5c0770cc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.