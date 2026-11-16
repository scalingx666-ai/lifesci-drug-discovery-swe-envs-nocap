# Issue

**Title:** Klekota-Roth prefix optimization

## Description

## Changes

- Completely rewrote the Klekota-Roth fingerprint computation for better performance.
- Replaced the naive O(n × m) loop over molecules and patterns with a tree-based traversal.
- Generated an efficient tree structure used by the algorithm and stored it in `tree.json`.
- Added atom-count-based filtering for faster pattern rejection.
- Removed the hardcoded list of 4860 patterns from the module; patterns are now loaded from the tree structure.
- Added a test verifying result correctness against the naive approach.

## Other notes
- `tree.json` is generated offline with a separate script (not included in this PR).
- Achieved a 6–9× performance boost for single-core execution and roughly a 5–7× boost for multicore, depending on dataset.

## Checklist before requesting a review
- [x] Docstrings added/updated in public functions and classes
- [x] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)
- [x] Sphinx docs added/updated and render properly (`make docs` and see `docs/_build/index.html`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ad559baee388`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.