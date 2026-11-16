# Issue

**Title:** Avoid Reprocessing for failed Inference

## Description

Currently, restarting a failed inference job requires inputs to be reprocessed again. 

This PR introduces a fix for the same by checking for the `manifest.json` file in the corresponding output directory, and only processing missing examples. The manifest is also updated accordingly to reflect this.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9d88b09392f0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.