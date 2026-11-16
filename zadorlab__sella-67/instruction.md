# Issue

**Title:** fix: switch to compatible setup using only `pyproject.toml` and `environment.yml`

## Description

This is a fix for issue #66, which breaks the install of `sella`, since the use of `pkg_resources` is deprecated. 

More info [here](https://setuptools.pypa.io/en/stable/history.html). 

- unified the dependencies in `pyproject.toml`
- fixed inconsistencies with `sella` between the `environment.yml` and the `pyproject.toml`
- remove redundant `requirements.txt`, since the `pyproject.toml` defines everything now
- moved the Cython build part in the `pyproject.toml`
- Tested setup with multiple Python versions

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c8a071c3cb0f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.