# Issue

**Title:** Py39 numpy1 build fix

## Description

## Issue Number
<!--- Is this pull request related to any outstanding issues? If so, list the issue number. --->


## Describe the changes made
<!--- A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it. -->
Hot fix for builds with Python 3.9, where numpy2 breaks pytables (but pytables 3.9.2 is listed as supported anyways).

## Goals and Outstanding Issues
<!--- A clear and concise list of goals (to be) accomplished. --->
- [x] Fix Python 3.9 builds 

## Major files changed
<!--- Manually list files or include a diff link in the form of: https://github.com/user/westpa/compare/<initial SHA>..<final SHA> --->
- [ ]

## Status
<!--- Delete bullet points that are not relevant. --->
- [x] Bug fix (non-breaking change which fixes an issue)
- [ ] New feature (non-breaking change which adds functionality)
- [ ] Breaking change (fix or feature that would cause existing functionality to change)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [x] My change requires a change to the documentation.
- [x] I have updated the documentation accordingly.
- [x] I have added tests to cover my changes.
- [x] All new and existing tests passed.

## Additional context
<!--- Add any other context or screenshots about the pull request here. --->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `55970507fab1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.