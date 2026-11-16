# Issue

**Title:** Streamline embedded dependencies

## Description

This PR ensures we load the same dependencies for the `implementation` and `embeddedKernel` configurations. Tests have also been added for the cases that prompted this change.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4e5c2e021d88`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.