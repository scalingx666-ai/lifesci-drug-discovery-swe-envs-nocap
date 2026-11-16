# Issue

**Title:** Sigstore attestations

## Description

Adds Sigstore attestations to PyPI releases, enabling users to cryptographically verify that published packages were built directly from the repository's CI pipeline.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eaf0915a32c9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.