# Issue

**Title:** fix case when west/executable/datasets is defined as None

## Description

## Issue Number
<!--- Is this pull request related to any outstanding issues? If so, list the issue number. --->
https://groups.google.com/g/westpa-users/c/QsCFwKACp70

## Describe the changes made
<!--- A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it. -->
If no dataset is set (i.e. [here](https://github.com/westpa/westpa_tutorials/tree/main/additional_tutorials/basic_nacl_gmx)), initialization will fail. That is when `west.executable.datasets` is listed but nothing is defined underneath. Example [here](https://github.com/westpa/westpa_tutorials/blob/35e20f3f39ef9a0b4c92251d9f36a408ff162c2c/additional_tutorials/basic_nacl_gmx/west.cfg#L42).


## Goals and Outstanding Issues
<!--- A clear and concise list of goals (to be) accomplished. --->
- [x] Fix case when "dataset" is set as None in west.cfg

## Major files changed
<!--- Manually list files or include a diff link in the form of: https://github.com/user/westpa/compare/<initial SHA>..<final SHA> --->
- [x] src/westpa/core/propagators/executable.py

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a3a674a8e96f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.