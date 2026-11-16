# Issue

**Title:** Fix atom-pair count ordering and hash lookups

## Description

Atom-pair count fingerprints return bins in hash-map order, although ICountFingerprint requires ascending hashes. Ethane and propane consequently score zero with count Tanimoto instead of one third.

Sort the bins by feature index. Hash lookups now check the features present in the molecule and return zero for absent features.

Tests cover similarity in both argument orders, present and missing hashes, and the existing phenol counts. Validation: mvn -o -q -pl descriptor/fingerprint -am clean test.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9101942edacb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.