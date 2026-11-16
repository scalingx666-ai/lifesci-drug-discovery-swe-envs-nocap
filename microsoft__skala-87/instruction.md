# Issue

**Title:** Fix sphinx build

## Description

The sphinx build was failing due to a bug in setting `max_memory` in `gen_response` while running on cpu. This PR fixes that by correctly fetching it from the ks object instead from the kwargs dict.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `029975d75ebb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.