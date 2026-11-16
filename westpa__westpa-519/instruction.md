# Issue

**Title:** Clean up of setup.py, Moving more to pyproject.toml

## Description

## Issue Number
<!--- Is this pull request related to any outstanding issues? If so, list the issue number. --->


## Describe the changes made
<!--- A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it. -->
Just a general cleanup of `setup.py`, moving most into `pyproject.toml`. Simple refactor and should have no observable effects on the user.

Most project info and dependencies are now in `pyproject.toml`.  The only stuff left in `setup.py` are the cythonize steps, `versioneer` and the entry points. The entry points were too big of a block and it's just cleaner to include/leave in `setup.py`.

## Goals and Outstanding Issues
<!--- A clear and concise list of goals (to be) accomplished. --->
- [x] Update install scripts to modern standards 

## Major files changed
<!--- Manually list files or include a diff link in the form of: https://github.com/user/westpa/compare/<initial SHA>..<final SHA> --->
- [x] setup.py
- [x] pyproject.toml

## Status
<!--- Delete bullet points that are not relevant. --->
- [x] New feature (non-breaking change which adds functionality)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.

- [x] All new and existing tests passed.

## Additional context
<!--- Add any other context or screenshots about the pull request here. --->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bf8b00564d45`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.