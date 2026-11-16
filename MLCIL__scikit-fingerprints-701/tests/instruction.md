# Issue

**Title:** Add element counts descriptor

## Description

## Changes

.

Adds element_counts(mol) to skfp.descriptors.constitutional, returning a 118-element NumPy array with atom counts for each element in the RDKit periodic table. The result can be used to describe a molecule's elemental composition or as a feature vector.

## Details

-Elements are ordered by atomic number, starting with hydrogen at index 0.

-Counts both implicit and explicit hydrogens, including molecules consisting only of hydrogen atoms.

-Ignores dummy atoms (atomic number 0).

-Returns a fixed-length np.ndarray with uint32 values.

-Exports the function through skfp.descriptors and adds it to the Sphinx documentation.

-Adds 14 parametrized test cases covering common molecules, explicit hydrogens, isotopes, ions, dummy atoms, and empty molecules. Tests compare the complete 118-element array.

## Checklist before requesting a review

- [x] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)

- [x] Docstrings added/updated in public functions and classes

- [x] Sphinx docs added/updated and render properly (make docs and see docs/_build/index.html)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8ff40d83f50b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.