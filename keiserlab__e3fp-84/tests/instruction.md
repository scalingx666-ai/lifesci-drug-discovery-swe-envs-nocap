# Issue

**Title:** Provide aliases for CLI scripts

## Description

This PR aliases `src/e3fp/conformer/generate.py` as a command `e3fp-conformer` and `src/e3fp/fingerprint/generate.py` as a command `e3fp-fingerprint`, both added to the user's path. This allows the scripts to be used just by installing e3fp into an environment without needing to work with the source code.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4fea3d6c3460`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.