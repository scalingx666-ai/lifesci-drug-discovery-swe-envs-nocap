# Issue

**Title:** Allow the ExtendedFingerprinter to setHashExplicitHydrogens

## Description

Suggestion from Andrew Dalke - the ExtendedFingerprint should be able to set the 'hash explicit hydrogen' option of the delegated path fingerprint.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c3ff083366d5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.