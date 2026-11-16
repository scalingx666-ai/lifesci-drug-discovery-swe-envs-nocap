# Issue

**Title:** Remove spyrmsd module in favor of __main__ function

## Description

## Description

As mentioned in #49, `from spyrmsd import spyrmsd` is confusing and potentially problematic. This PR removes the `spyrmsd` module in favor of `__main__.py`.

Important changes:
* `rmsdwrapper` is now in the `spyrmsd.rmsd` module
* `coords_from_molecule` is now in `spyrmsd.molecule`
* The standalone tool now needs to be invoked as follows: `python -m spyrmsd -h` instead of `python -m spyrmsd.spyrmsd -h`

## Checklist

- [x] Tests
- [x] Documentation

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `652b44d98c8f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.