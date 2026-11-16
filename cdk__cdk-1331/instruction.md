# Issue

**Title:** Implement substructure count fingerprint operations

## Description

Substructure and Klekota–Roth count fingerprints silently ignore merge and binary-view requests. With custom C and O SMARTS keys, methane and ethane still score 0.5 after selecting binary comparison, instead of 1.

Binary views and count merging now follow `IntArrayCountFingerprint` semantics. Stored counts remain available through `getCountForHash`, and feature indices remain sorted.

Tests cover binary similarity, overlapping and disjoint features, self-merges, binary inputs and Klekota–Roth behaviour. The first commit contains the failing regression tests; the second implements the fix.

`mvn -o -q -pl descriptor/fingerprint -am test` passes.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9101942edacb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.