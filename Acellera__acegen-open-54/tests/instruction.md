# Issue

**Title:** fix acegen to tested versions of torchrl and tensordict

## Description

- Moved requirements in README to requirements.txt
- RDKit is now a required dependency otherwise tests fail
- TorchRL and Tensordict fixed to tested versions using git commit hashes

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `551ba16c4d42`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.