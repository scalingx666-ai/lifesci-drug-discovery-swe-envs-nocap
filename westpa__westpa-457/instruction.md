# Issue

**Title:** Fix w_init when using hdf5 framework with processes work manager

## Description

## Issue Number
<!--- Is this pull request related to any outstanding issues? If so, list the issue number. --->
#456 

## Describe the changes made
<!--- A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it. -->
Copy the entire BasisState object from work manager during pcoord calculations instead of just the pcoord.

## Goals and Outstanding Issues
<!--- A clear and concise list of goals (to be) accomplished. --->
- [x] Have w_init work correctly with hdf5 framework + processes work manager

## Major files changed
<!--- Manually list files or include a diff link in the form of: https://github.com/user/westpa/compare/<initial SHA>..<final SHA> --->
- [x] src/westpa/core/sim_manager.py

## Status
<!--- Delete bullet points that are not relevant. --->
- [x] Bug fix (non-breaking change which fixes an issue)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [x] I have updated the documentation accordingly.
- [x] I have added tests to cover my changes.
- [x] All new and existing tests passed.

## Additional context
<!--- Add any other context or screenshots about the pull request here. --->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5cfa0382f0cd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.