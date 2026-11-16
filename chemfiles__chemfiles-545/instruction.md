# Issue

**Title:** Reject out-of-range atom indices in add_residue

## Description

## Summary

.

This report is part of our study on testing chemical software repositories with scenario-specific, chemistry-aware invariants. `Topology::add_residue()` accepted atom indices outside the topology and created residue metadata for atoms that did not exist.

The existing fork branch already includes the related mutation-mapping repair from #539. This change adds the missing bounds check and a regression test. The check runs before any mapping is inserted, so a rejected residue leaves the topology unchanged.

## Validation

The reproducer now raises `OutOfBounds`, while valid residue membership continues to work. The change is covered by `tests/topology.cpp`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `582e6da1ce7c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.