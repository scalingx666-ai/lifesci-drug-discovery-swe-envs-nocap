# Issue

**Title:** CI security update

## Description

## Changes

1. Replaced PyPI API keys with [Trusted Publishing](https://github.com/lirantal/pypi-security-best-practices#11-publish-with-trusted-publishing-oidc)
2. Added [package attestations](https://github.com/lirantal/pypi-security-best-practices#12-publish-with-package-attestations) to published packages. This required replacing `uv publish` with PyPA action.
3. Pinned [GH Actions to SHA hashes](https://github.com/lirantal/pypi-security-best-practices#13-secure-your-cicd-release-pipeline) instead of just major release tag.
4. Specified GH Actions permissions where they were missing.
5. Added [zizmor](https://github.com/zizmorcore/zizmor) for GH Actions static analysis.
6. Updated dependencies, fixed mypy problems where necessary.
7. Added `uv audit` to verify local packages for maintainers.

This obviously affects publishing, so we should test this with next release.

## Checklist before requesting a review
- [x] Docstrings added/updated in public functions and classes
- [x] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)
- [x] Sphinx docs added/updated and render properly (`make docs` and see `docs/_build/index.html`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `188524395d52`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.