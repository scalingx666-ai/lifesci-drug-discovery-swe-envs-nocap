# Issue

**Title:** Support multiline attributes

## Description

PubChem and other databases export SDFiles with multiline attributes.
This reads such attributes as a list of strings.

This also recognizes $$$$ as a compound-terminator. However, this does
not yet properly support multi-compound SDFiles.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `90d6f6175f30`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.