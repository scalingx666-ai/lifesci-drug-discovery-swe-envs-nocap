# Issue

**Title:** Simplify Python setup process

## Description

This should allow to install the Python API with pip using

```
pip install "https://github.com/dftd4/dftd4/archive/refs/heads/main#egg=dftd4-python&subdirectory=python"
```

It will require an existing `dftd4` installation, though. Chances for success can be improved by installing `pkgconfig`, setting `DFTD4_PREFIX` to the directory where the installation can be found or providing a C compiler in the `CC` environment variable. None of those are mandatory as we try to fall back to reasonable defaults, but those defaults might not be where `dftd4` is actually installed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `776f8af9b975`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.