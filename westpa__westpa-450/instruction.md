# Issue

**Title:** Enable testing for Python 3.13

## Description

## Issue Number
<!--- Is this pull request related to any outstanding issues? If so, list the issue number. --->
#451 

## Describe the changes made
<!--- A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it. -->
Python 3.13 was released October 7th, 2024. Adding testing for python 3.13. We're obviously not ready because `mdtraj` is not python 3.13-ready just yet (We're working on it!). Everything else looks fine though.

## Goals and Outstanding Issues
<!--- A clear and concise list of goals (to be) accomplished. --->
- [x] Enable testing for python 3.13

## Major files changed
<!--- Manually list files or include a diff link in the form of: https://github.com/user/westpa/compare/<initial SHA>..<final SHA> --->
- [x] See below.

## Status
<!--- Delete bullet points that are not relevant. --->
- [x] New feature (non-breaking change which adds functionality)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [x] My change requires a change to the documentation.
- [x] I have updated the documentation accordingly.
- [x] I have added tests to cover my changes.
- [x] All new and existing tests passed.

## Additional context
<!--- Add any other context or screenshots about the pull request here. --->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `09aba07e2557`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.