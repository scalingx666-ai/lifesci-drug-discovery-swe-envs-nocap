# Issue

**Title:** Add Mordred WalkCount descriptor

## Description

This pull request introduces the new `walk_count` descriptor to the NewMordred fingerprint calculation.

New Features:

Added the `walk_count` descriptor, which computes 21 topological walk-based features: molecular walk counts (MWC01–MWC10), their cumulative total (`TMWC10`), self-returning walk counts (`SRW02`–`SRW10`), and their cumulative total (`TSRW10`). These descriptors encode the structural complexity of a molecule by counting paths of increasing length in the molecular graph, derived from successive powers of the adjacency matrix.

## Checklist before requesting a review
- [ ] Docstrings added/updated in public functions and classes
- [x] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)
- [ ] Sphinx docs added/updated and render properly (`make docs` and see `docs/_build/index.html`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c0e6b54928cc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.