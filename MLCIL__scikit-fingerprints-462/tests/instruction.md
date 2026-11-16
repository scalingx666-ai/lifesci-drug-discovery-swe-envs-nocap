# Issue

**Title:** Docs hosting at ReadTheDocs

## Description

## Changes

Currently, the docs are hosted at Github.io. This PR moves it to ReadTheDocs, including GitHub integration, so that we have versioning and automated builds for new releases. It hosts "latest", "stable" and previous version branches. Closes 

## Checklist before requesting a review
- [x] Docstrings added/updated in public functions and classes
- [x] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)
- [x] Sphinx docs added/updated and render properly (`make docs` and see `docs/_build/index.html`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8041476abde9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.