# Issue

**Title:** Add Mordred AdjacencyMatrix descriptor

## Description

This pull request introduces the new `adjacency_matrix` descriptor to the NewMordred fingerprint calculation.

New Features:

Added the `adjacency_matrix` descriptor, which computes 12 spectral features derived from the molecular adjacency matrix: graph energy (`SpAbs_A`), leading eigenvalue (`SpMax_A`), spectral diameter (`SpDiam_A`), spectral absolute and mean absolute deviation `(SpAD_A`, `SpMAD_A`), Estrada-like index (`LogEE_A`), eigenvector-based coefficients (`VE1_A`–`VE3_A`), and Randić-like eigenvector indices `(VR1_A`–`VR3_A`). These descriptors capture the electronic and topological structure of a molecule through the eigenspectrum of its graph representation.

## Checklist before requesting a review
- [ ] Docstrings added/updated in public functions and classes
- [x] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)
- [ ] Sphinx docs added/updated and render properly (`make docs` and see `docs/_build/index.html`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `964ce2b7791e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.