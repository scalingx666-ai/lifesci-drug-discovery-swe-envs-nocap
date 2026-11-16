# Issue

**Title:** Fix symmetry scoring with current NetworkX

## Description

Correct the bond matcher defaults so their count matches the bond attributes. This restores the core symmetry tests and Functional API notebook across the current CI matrix.

Validated locally on Python 3.14 and RDKit 2026.3: 93 core tests passed, and the previously failing Functional API notebook passed. Includes the 2.1.1 changelog entry for a patch release.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `decda0c25aee`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.