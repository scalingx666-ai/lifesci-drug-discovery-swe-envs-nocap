# Issue

**Title:** Restore molecular mass bits in ExtendedFingerprinter

## Description

`ExtendedFingerprinter` uses natural abundance instead of molecular mass, leaving the mass-range bits unset for ordinary molecules. The calculation now uses molecular mass for the existing thresholds.

The tests compare molecules with the same path features within one mass range and across the 200 Da boundary. Carbon-13 labelling also crosses that boundary without changing the topology. The regression tests are in the first commit; the fix follows separately. The existing ring comparison excludes mass bits.

`mvn -o -pl descriptor/fingerprint -am clean test` passes. Stored bit fingerprints need regenerating to include the restored mass features.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `96e194ce4aed`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.