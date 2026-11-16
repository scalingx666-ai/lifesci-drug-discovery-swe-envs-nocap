# Issue

**Title:** force x86-64 macos GitHub Action Runners

## Description

## Issue Number
<!--- Is this pull request related to any outstanding issues? If so, list the issue number. --->


## Describe the changes made
<!--- A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it. -->
If you noticed, the CI tests are failing because some header files are not found. This is due to how `macos-latest` runners now default to the arm64 versions, since 2024-04-22.

https://github.com/actions/runner-images

## Goals and Outstanding Issues
<!--- A clear and concise list of goals (to be) accomplished. --->
- [x] Fix CI by pinning to macos-13 (last non-arm64 macos standard runner)
- [x] Drop Python 3.7 testing
- [x] Some flake8 lint caught by the pre-commit runner (but not the GH Action linter).

## Major files changed
<!--- Manually list files or include a diff link in the form of: https://github.com/user/westpa/compare/<initial SHA>..<final SHA> --->
- [x] .github/workflows/test.yaml
- [x] .github/workflows/build.yaml
- [x] src/westpa/core/sim_manager.py
- [x] src/westpa/westext/hamsm_restarting/restart_driver.py

## Status
<!--- Delete bullet points that are not relevant. --->
- [x] Bug fix (non-breaking change which fixes an issue)
- [x] I have read the CONTRIBUTING document.

## Additional context
<!--- Add any other context or screenshots about the pull request here. --->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `21d00b338132`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.