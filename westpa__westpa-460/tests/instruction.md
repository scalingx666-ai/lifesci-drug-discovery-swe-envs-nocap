# Issue

**Title:** RNG Modernization

## Description

## Issue Number
<!--- Is this pull request related to any outstanding issues? If so, list the issue number. --->


## Describe the changes made
<!--- A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it. -->
This PR isolate the RNG from the global `random` and/or `np.random` modules into independent `numpy.random.Generator` (see [here](https://numpy.org/doc/stable/reference/random/index.html)), protecting the key portions of WESTPA from other programs that might seed the RNG irresponsibly. For the sake of consistency, we will continue to use the MT19937 algorithm.

The RNG in Cythonized parts are not replaced because an independent `numpy.random.Generator` requires locking the GIL every time you request a number, and that's just not efficient.

The fasthist testing script `/src/westpa/fasthist/__main__.py` has been refactored into `test_fasthist.py`, to show/test that it's faster than `numpy.histogramdd`.


## Goals and Outstanding Issues
<!--- A clear and concise list of goals (to be) accomplished. --->
- [x] Modernize and isolate WESTPA RNG
- [x] Refactor /src/westpa/fasthist/__main__.py into test_fasthist.py

## Major files changed
<!--- Manually list files or include a diff link in the form of: https://github.com/user/westpa/compare/<initial SHA>..<final SHA> --->
- [x] src/westpa/core/propagators/executable.py
- [x] src/westpa/core/we_driver.py
- [x] and other tests and old tools (see below)

## Status
<!--- Delete bullet points that are not relevant. --->
- [x] Bug fix (non-breaking change which fixes an issue)
- [x] New feature (non-breaking change which adds functionality)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [x] My change requires a change to the documentation.
- [ ] I have updated the documentation accordingly.
- [x] I have added tests to cover my changes.
- [x] All new and existing tests passed.

## Additional context
<!--- Add any other context or screenshots about the pull request here. --->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8223b1fa625f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.