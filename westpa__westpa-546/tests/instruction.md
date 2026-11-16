# Issue

**Title:** Add Python 3.14 back into cibuildwheels workflow

## Description

## Issue Number
<!--- Is this pull request related to any outstanding issues? If so, list the issue number. --->
Reverts #530

## Describe the changes made
<!--- A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it. -->
Try and build Python 3.14 wheels.

Problems were mostly in testing the wheels: installing `pytables` in the venv is a pain because of the lack of wheels for Python 3.14.
I got around by installing `hdf5/hdf5-devel` and installing `python-blosc2` (because blosc2 isn't available for Alma Linux 8 from regular channels). I also had to install from github source for python 3.14 because of a bug in Pytables 3.10.2 source.

## Goals and Outstanding Issues
<!--- A clear and concise list of goals (to be) accomplished. --->
- [x] Build python 3.14 wheels

## Major files changed
<!--- Manually list files or include a diff link in the form of: https://github.com/user/westpa/compare/<initial SHA>..<final SHA> --->
- [x] .github/workflows/build.yaml

## Status
<!--- Delete bullet points that are not relevant. --->
- [x] Bug fix (non-breaking change which fixes an issue)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [x] My change requires a change to the documentation.
- [x] I have updated the documentation accordingly.
- [x] I have added tests to cover my changes.
- [x] All new and existing tests passed.

## Additional context
<!--- Add any other context or screenshots about the pull request here. --->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `da43dd342ba6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.