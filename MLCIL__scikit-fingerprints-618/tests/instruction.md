# Issue

**Title:** Mordred Barysz matrix

## Description

## Changes

This pull request introduces the `barysz_matrix` descriptor to the NewMordred fingerprint calculation and extends the atomic properties registry used across descriptors.

New Features:

Added the barysz_matrix descriptor, which computes 104 spectral features (13 attributes × 8 atomic properties). The Barysz matrix is a weighted distance matrix where edge weights between bonded atoms are inversely proportional to their atomic property values and bond order, normalized against the corresponding carbon–carbon value. Shortest paths are resolved via the Floyd–Warshall algorithm. Spectral attributes (SpAbs, SpMax, SpDiam, SpAD, SpMAD, LogEE, SM1, VE1–VE3, VR1–VR3) are computed for each of the 8 atomic properties (Z, m, v, se, pe, are, p, i). All features are set to NaN for disconnected molecules.

Added PROPERTY_FUNCS dictionary to atomic_properties.py, mapping short property names ("Z", "m", "v", etc.) to their corresponding atom getter functions. This replaces the legacy _AUTOCORRELATION_PROPERTY_FUNCS pattern and provides a shared registry for descriptors that need lookup by short name.

## Checklist before requesting a review
- [ ] Docstrings added/updated in public functions and classes
- [ ] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)
- [ ] Sphinx docs added/updated and render properly (`make docs` and see `docs/_build/index.html`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6627a5d712b2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.