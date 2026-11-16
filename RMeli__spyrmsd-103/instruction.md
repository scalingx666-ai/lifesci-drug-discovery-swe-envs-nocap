# Issue

**Title:** Update build system to flit_core

## Description

Hi, I'm opening this pull request as part of a push to modernise how packages use [Flit](https://flit.pypa.io/en/stable/) as a Python build backend.

Using `flit_core` as the backend in place of `flit` is [recommended in the docs](https://flit.pypa.io/en/stable/pyproject_toml.html#build-system-section), and will make it faster for tools like pip & [build](https://build.pypa.io/en/latest/) to build your package from source, as it has fewer dependencies to install.

Specifying an explicit version range (`>=2,<4`) helps to ensure that your package can still be readily built from source despite changes in future major versions of Flit, because it will still use version 3.x. For instance, a future version is likely to drop support for the `[tool.flit.metadata]` table, in favour of the now-standardised `[project]` table for metadata. This is also [in the docs](https://flit.pypa.io/en/stable/pyproject_toml.html#build-system-section), along with details of which versions support which features.

Most users probably install your package from a pre-built 'wheel' on PyPI, so this changes won't affect them at all. But people who install from a git checkout, for instance, will benefit.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d50f2037e796`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.