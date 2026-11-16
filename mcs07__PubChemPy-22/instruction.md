# Issue

**Title:** Decode CACTVS fingerprint to binary string

## Description

Decode fingerprint using method by @RickardSjogren in #21 but put in a separate `cactvs_fingerprint` method to maintain backwards compatibility with the `fingerprint` method.

Replaces #21

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cd10378fb649`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.