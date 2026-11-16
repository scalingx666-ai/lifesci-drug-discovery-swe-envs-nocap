# Issue

**Title:** OpenBabel and RDKit constructors

## Description

## Description

Fix #41; it is now possible to build a `spyrmsd.molecule.Molecule` directly from an OpenBabel or RDKit molecules.

This PR also solves a unreported problem where `to_molecule` would fail with `adjacency=False` (which was not tested).

Some changes are introduced for compatibility with the latest version of `mypy`.

## Checklist

- [x] Tests
- [x] Documentation

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f490dc16dd41`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.