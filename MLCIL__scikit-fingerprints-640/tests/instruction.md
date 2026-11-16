# Issue

**Title:** Add Adam as maintainer

## Description

## Changes

@StaniszewskiA is one of the maintainers and authors, so he should be in the CODEOWNERS file.

## Checklist before requesting a review
- [ ] Docstrings added/updated in public functions and classes
- [ ] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)
- [ ] Sphinx docs added/updated and render properly (`make docs` and see `docs/_build/index.html`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e504f0aee682`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.