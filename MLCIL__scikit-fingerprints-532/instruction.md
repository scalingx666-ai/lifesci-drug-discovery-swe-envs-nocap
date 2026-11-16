# Issue

**Title:** Fixed random_state parameter documentation and implementation

## Description

## Changes



Implemented fix for the issue described. All tests pass.

- Removed random_state from BaseFingerprintTransformer and BaseSubstructureFingerprint
- Added random_state parameter to MAPFingerprint, MHFPFingerprint, and SECFPFingerprint
- Added missing documentation for random_state in affected classes
- Removed random_state from E3FPFingerprint as it doesn't use randomness
- Updated FingerprintEstimatorRandomizedSearch documentation

## Checklist before requesting a review
- [ ] Docstrings added/updated in public functions and classes
- [ ] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)
- [ ] Sphinx docs added/updated and render properly (`make docs` and see `docs/_build/index.html`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e78407cfa923`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.