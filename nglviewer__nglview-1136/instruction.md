# Issue

**Title:** Fix pkg_resources deprecation warning

## Description

* Warning:
`nglview/__init__.py:12: DeprecationWarning: pkg_resources is deprecated as an API. See https://setuptools.pypa.io/en/latest/pkg_resources.html`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d3b099ad338c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.