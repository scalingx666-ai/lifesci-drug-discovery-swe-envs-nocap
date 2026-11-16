# Issue

**Title:** Add Mordred AcidBase descriptor

## Description

This pull request introduces the new `acid_base` descriptor to the NewMordred fingerprint calculation and updates related documentation and tests. It also makes minor documentation fixes for the Zagreb index descriptors.

**New Features:**

* Added the `acid_base` descriptor, which computes counts of acidic and basic groups, to the NewMordred fingerprint.

**Documentation and Test Improvements:**

* Updated docstring examples for `zagreb_index_m1` and `zagreb_index_m2` to show floating-point results and fixing the pipeline.
* Fixed a docstring formatting issue in the `NewMordredFingerprint` example output.

## Checklist before requesting a review
- [x] Docstrings added/updated in public functions and classes
- [x] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)
- [x] Sphinx docs added/updated and render properly (`make docs` and see `docs/_build/index.html`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f91e9d39fd5a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.