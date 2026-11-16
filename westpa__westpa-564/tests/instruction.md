# Issue

**Title:** Simplify py3.14 wheel building workflow

## Description

## Issue Number
<!--- Is this pull request related to any outstanding issues? If so, list the issue number. --->
Reverts/simplify work around from #555 #546

## Describe the changes made
<!--- A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it. -->
Now that Pytables 3.11.0 (with wheels for python 3.14) is finally released, we don't have to use our workaround for Python 3.14/macOS wheel building.

https://github.com/jeremyleung521/westpa/actions/runs/22416392701

## Goals and Outstanding Issues
<!--- A clear and concise list of goals (to be) accomplished. --->
- [x] simplify wheel-building matrix 

## Major files changed
<!--- Manually list files or include a diff link in the form of: https://github.com/user/westpa/compare/<initial SHA>..<final SHA> --->
- [x] .github/workflows/build.yaml

## Status
<!--- Delete bullet points that are not relevant. --->
- [x] Bug fix (non-breaking change which fixes an issue)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [x] I have updated the documentation accordingly.
- [x] I have added tests to cover my changes.
- [x] All new and existing tests passed.
- [x] I have read the AI POLICY document.
- [x] This PR conforms to WESTPA's AI policy.
- [x] I have declared all usage of AI in the PR description.

## Additional context
<!--- Add any other context or screenshots about the pull request here. --->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f24f6e97f635`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.