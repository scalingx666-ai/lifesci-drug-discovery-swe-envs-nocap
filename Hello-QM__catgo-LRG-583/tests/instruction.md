# Issue

**Title:** chore: encrypt one-time release secret export

## Description

Replaces the direct cross-repository token approach with a one-time GPG-encrypted artifact. Only the local ephemeral private key can decrypt it; secret values are never logged.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `09e932d034c1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.