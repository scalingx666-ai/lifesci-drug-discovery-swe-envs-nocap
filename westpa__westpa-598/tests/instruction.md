# Issue

**Title:** Compatibility to Numpy >= 2.5.0

## Description

## Issue Number
<!--- Is this pull request related to any outstanding issues? If so, list the issue number. --->
#597 

## Describe the changes made
<!--- A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it. -->
This patches compatibility to numpy 2.5.0. Further fixes (such as potentially swapping to histogramdd, rewriting the test) will be implemented in a different PR.

## Goals and Outstanding Issues
<!--- A clear and concise list of goals (to be) accomplished. --->
- [x] Make things work in Numpy >=2.5.0
- [x] Update Readthedocs building to miniforge3

## Major files changed
<!--- Manually list files or include a diff link in the form of: https://github.com/user/westpa/compare/<initial SHA>..<final SHA> --->
- [x] src/westpa/core/_rc.py
- [x] tests/test_fasthist.py
- [x] src/westpa/core/binning/assign.py
- [x] src/westpa/core/propagators/loaders.py
- [x] tests/test_binning.py
- [x] .readthedocs.yml

## Status
<!--- Delete bullet points that are not relevant. --->
- [x] Bug fix (non-breaking change which fixes an issue)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [x] My change requires a change to the documentation.
- [x] I have updated the documentation accordingly.
- [x] I have added tests to cover my changes.
- [x] All new and existing tests passed.
- [x] I have read the AI POLICY document.
- [x] This PR conforms to WESTPA's AI policy.
- [x] I have declared all usage of AI in the PR description.

## Additional context
<!--- Add any other context or screenshots about the pull request here. --->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4a076930878a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.