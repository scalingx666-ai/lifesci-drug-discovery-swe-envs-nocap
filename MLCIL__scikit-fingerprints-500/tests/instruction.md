# Issue

**Title:** Update Sphinx build

## Description

## Changes

- Added multithreading to sphinx build options (default all cores)
  - 50+% speedup (`47.00 ± 0.24` seconds to `20.23 ± 0.30` seconds. M3 Pro 5 samples)
- Removed `clean` from build due to lack of issues.

If there any reproducibility steps for issues with non-clean builds for docs, please let me know.

## Checklist before requesting a review
- [x] Docstrings added/updated in public functions and classes
- [x] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)
- [x] Sphinx docs added/updated and render properly (`make docs` and see `docs/_build/index.html`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fd105a849d24`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.