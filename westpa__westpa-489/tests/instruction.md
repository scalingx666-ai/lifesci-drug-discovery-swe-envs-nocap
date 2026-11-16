# Issue

**Title:** Doc fix for westpa.analysis and westpa.core.propagators

## Description

## Issue Number
<!--- Is this pull request related to any outstanding issues? If so, list the issue number. --->
 
fixes 

## Describe the changes made
<!--- A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it. -->
Remove unnecessary documentation and fix broken link from RTD

## Goals and Outstanding Issues
<!--- A clear and concise list of goals (to be) accomplished. --->
- [x] Remove redundant and unnecessary auto docstrings
- [x] fix broken link in westpa.analysis.trajectories

## Major files changed
<!--- Manually list files or include a diff link in the form of: https://github.com/user/westpa/compare/<initial SHA>..<final SHA> --->
- [x] doc/documentation/core/westpa.core.propagators.rst
- [x] src/westpa/analysis/trajectories.py

## Status
<!--- Delete bullet points that are not relevant. --->
- [x] Bug fix (non-breaking change which fixes an issue)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [x] My change requires a change to the documentation.
- [x] I have updated the documentation accordingly.
- [x] All new and existing tests passed.

## Additional context
<!--- Add any other context or screenshots about the pull request here. --->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `463f24692160`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.