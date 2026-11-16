# Issue

**Title:** Fix python3.12 build failure

## Description

This *should* fix 

`setuptools` is now a required build dependency for Python 3.12, see https://cffi.readthedocs.io/en/stable/whatsnew.html#v1-16-0.

It wasn't super clear to me how the wheels that land on PyPI are generated. To test this I downloaded the current source distribution, modified the `pyproject.toml` file, and tested that the installation works.
Someone needs to make sure that this also works with your workflow/in the CI.

The same patch should be applicable to [dftd4](https://github.com/dftd4/dftd4/blob/main/python/pyproject.toml#L2) and [tblite](https://github.com/dftd4/dftd4/blob/main/python/pyproject.toml#L2).

Linked issues for reference:  

While at it, I have also updated the usage of random calls to replace some deprecated function calls.

*I will have no access to the internet for the next two weeks and probably won't reply on this PR, sorry for that.*

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f147b265d8b5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.