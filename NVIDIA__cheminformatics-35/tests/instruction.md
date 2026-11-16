# Issue

**Title:** Bugfix: ChEMBLE DB download function should use versioned URL...

## Description

EBI upgrade to v28 caused our dbsetup script to fail. This change hardcodes the
version, instead of using 'latest' URL.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `81f7d7215f22`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.