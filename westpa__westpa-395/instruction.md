# Issue

**Title:** W_succ ignores -W argument

## Description

## Issue Number
<!--- Is this pull request related to any outstanding issues? If so, list the issue number. --->
N/A

## Describe the changes made
<!--- A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it. -->
`w_succ` currently ignores the `-W` argument (despite accepting it) because of a typo in `WESTDataReaderMixin`. Probably affects `w_ttimes` as well, but I haven't seen anyone actually use that tool.

`backing_file` is currently NOT an attribute of the `data_manager` so no other consequences stems from this change.

## Goals and Outstanding Issues
<!--- A clear and concise list of goals (to be) accomplished. --->
- [x]  Have `w_succ` respect the h5file name given

## Major files changed
<!--- Manually list files or include a diff link in the form of: https://github.com/user/westpa/compare/<initial SHA>..<final SHA> --->
- [x]  src/westpa/oldtools/aframe/data_reader.py

## Status
<!--- Delete bullet points that are not relevant. --->
- [x] Bug fix (non-breaking change which fixes an issue)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [x] All new and existing tests passed.

## Additional context
<!--- Add any other context or screenshots about the pull request here. --->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ae52414ff3a4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.