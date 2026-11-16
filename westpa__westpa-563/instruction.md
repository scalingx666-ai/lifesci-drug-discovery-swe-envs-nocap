# Issue

**Title:** Add w_red test + small style fixes to w_red

## Description

## Issue Number
<!--- Is this pull request related to any outstanding issues? If so, list the issue number. --->
#207 

## Describe the changes made
<!--- A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it. -->
Add testing for `w_red`. This only makes sure the code runs to completion and nothing on the actual accuracy.

The `w_red` code also loads in the rc way too early, so I moved it to somewhere where the tests can actually inject arguments in the RC config. Also curbed the try/excepts in the `w_red` code.



## Goals and Outstanding Issues
<!--- A clear and concise list of goals (to be) accomplished. --->
- [x] fix so w_red loads the rc only when 'go' is executed
- [x] Add prelim test for `w_red` 

## Major files changed
<!--- Manually list files or include a diff link in the form of: https://github.com/user/westpa/compare/<initial SHA>..<final SHA> --->
- [x] src/westpa/cli/tools/w_red.py
- [x] tests/conftest.py
- [x] tests/refs/west_ref.cfg
- [x] tests/test_tools/test_w_red.py

## Status
<!--- Delete bullet points that are not relevant. --->
- [x] Bug fix (non-breaking change which fixes an issue)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [x] I have added tests to cover my changes.
- [x] All new and existing tests passed.
- [x] I have read the AI POLICY document.
- [x] This PR conforms to WESTPA's AI policy.
- [x] I have declared all usage of AI in the PR description.

## Additional context
<!--- Add any other context or screenshots about the pull request here. --->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5027324172ec`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.