# Issue

**Title:** Retain fingerprint paths when atom identity hashes collide

## Description

Distinct atoms can share an identity hash. `Fingerprinter` can then skip both directions of a path, omitting features from bit, raw and count fingerprints. `GraphOnlyFingerprinter` and `HybridizationFingerprinter` share the affected encoder.

Container indices now select one traversal of each undirected path. The existing atom and bond comparisons still determine the encoded direction.

`mvn -o -pl descriptor/fingerprint -am clean test` passes, including the existing atom and bond permutation tests and raw/count checks. Compiled with the project's Java 8 release configuration.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `31b33146b0ca`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.