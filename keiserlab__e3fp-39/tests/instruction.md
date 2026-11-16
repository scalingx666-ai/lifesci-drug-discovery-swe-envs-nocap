# Issue

**Title:** Make compatible with latest Python versions

## Description

A few changes:
- Make Cython a required dependency (for now)
- Use conda-forge mmh3 instead of keiserlab's to avoid coercion to lower Python versions
- Install `python_utilities` via pip, even in `conda` (for now)
- test only last 3 versions of Python 3 on linux
- Increment version number (for future release and to avoid confusion of latest docs with v 1.1 docs)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e168d00ca029`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.