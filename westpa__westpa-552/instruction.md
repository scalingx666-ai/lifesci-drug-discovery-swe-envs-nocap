# Issue

**Title:** Remove pytest filter warning + test.yaml deprecated key "auto_activate_base" removal

## Description

## Issue Number
<!--- Is this pull request related to any outstanding issues? If so, list the issue number. --->


## Describe the changes made
<!--- A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it. -->
After countless tests, it's impossible to remove those DeprecationWarnings from numpy (I assume the fault is on numpy or pytest).

https://docs.pytest.org/en/7.1.x/how-to/capture-warnings.html#deprecationwarning-and-pendingdeprecationwarning

Dropping it completely

## Goals and Outstanding Issues
<!--- A clear and concise list of goals (to be) accomplished. --->
- [x] removing the deprecationwarning filter from pyproject.toml
- [x] drop the auto_activate_base deprecated key from test.yaml

## Major files changed
<!--- Manually list files or include a diff link in the form of: https://github.com/user/westpa/compare/<initial SHA>..<final SHA> --->
- [x] pyproject.toml
- [x] .github/workflows/test.yaml

## Status
<!--- Delete bullet points that are not relevant. --->
- [x] Bug fix (non-breaking change which fixes an issue)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [x] All new and existing tests passed.

## Additional context
<!--- Add any other context or screenshots about the pull request here. --->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d4fc6b0b6597`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.