# Issue

**Title:** Don't advertise support for older Python versions

## Description

380c82be01aafc7c1351a33f05d870d8ea2480cd added a `python_reqiures` of >= 3.6, but the classifiers are still checked when determining which Python versions are supported. Without this change, `python3.5 -m pip install nglview` still allows me to install the package without warnings.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a39ed7bce5f8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.