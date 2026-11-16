# Issue

**Title:** Clarified the aISS output

## Description

The `fast mode` printed in the output does not refer to the `--fast` flag, but to the use of the ATM term. This was clarified with the commit.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7b9935b95138`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.