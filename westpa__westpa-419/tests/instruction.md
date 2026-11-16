# Issue

**Title:** Allow w_init to save bin_mapper stuff to iteration 1

## Description

## Issue Number
<!--- Is this pull request related to any outstanding issues? If so, list the issue number. --->


## Describe the changes made
<!--- A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it. -->

Logic for `w_init` is different to `w_run` in that it doesn't save the bin mapper for iteration 1. This new PR will result in a behavior where `bin_target_count` dataset and corresponding `bin_topology` hash/pickle will be created for iteration 1.

## Goals and Outstanding Issues
<!--- A clear and concise list of goals (to be) accomplished. --->
- [x] Make iteration 1 more consistent with later iterations

## Major files changed
<!--- Manually list files or include a diff link in the form of: https://github.com/user/westpa/compare/<initial SHA>..<final SHA> --->
- [x] src/westpa/core/sim_manager.py

## Status
<!--- Delete bullet points that are not relevant. --->
- [x] Bug fix (non-breaking change which fixes an issue)
- [x] New feature (non-breaking change which adds functionality)
- [x] Breaking change (fix or feature that would cause existing functionality to change)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [x] My change requires a change to the documentation.
- [x] I have updated the documentation accordingly.
- [x] All new and existing tests passed.

## Additional context
<!--- Add any other context or screenshots about the pull request here. --->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ee8f5aba03ba`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.