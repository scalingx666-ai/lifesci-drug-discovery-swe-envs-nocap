# Issue

**Title:** Adjust benchmarking code to changed interfaces

## Description

## Changes

- _benchmarking/benchmark.py_ blocked by ,
- _benchmarking/fp_tuning.py_ adjusted ECFP changes, also added filtering out data empty data,
- _skfp/bases/base_fp_transformer_ had a bug where the PhysiochemicalProperties fingerprint was not properly cast to binary before calling __hash_fingerprint_bits_, causing an overflow.

## Checklist before requesting a review
- [x] Docstrings added/updated in public functions and classes
- [x] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)
- [x] Sphinx docs added/updated and render properly (`make docs` and see `docs/_build/index.html`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e26f390818d2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.