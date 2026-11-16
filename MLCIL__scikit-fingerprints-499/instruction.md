# Issue

**Title:** Add MoleculeACE datasets

## Description

## Changes

This pull request adds datasets for ChEMBL properties prediction along with activity cliffs splits from [MoleculeACE](https://github.com/molML/MoleculeACE).

For references, please see the article:

[D. van Tilborg, A. Alenicheva, and F. Grisoni
“Exposing the Limitations of Molecular Machine Learning with Activity Cliffs”
Journal of Chemical Information and Modeling, vol. 62, no. 23, pp. 5938–5951, Dec. 2022](https://doi.org/10.1021/acs.jcim.2c01073)

## Checklist before requesting a review
- [x] Docstrings added/updated in public functions and classes
- [x] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)
- [x] Sphinx docs added/updated and render properly (`make docs` and see `docs/_build/index.html`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fd105a849d24`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.