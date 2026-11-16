# Issue

**Title:** small CI workflow update

## Description

## Issue Number
<!--- Is this pull request related to any outstanding issues? If so, list the issue number. --->
Addendum to #472 

## Describe the changes made
<!--- A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it. -->
Only allow dispatch for mirror.yaml to run on `westpa2` branch. Doesn't really matter too much, since the workflow is hard coded to sync `develop` --> `westpa2`, but does simplify the amount of clicks if you want to rerun.

Also added the ability to manually start test.yaml and build.yaml from GH.

This also restructures the workflows so `upload_testpypi` will always execute before `upload_pypi`. The previous setup had little to no advantage and the `upload_testpypi` workflow always finished after it's reached the production pypi servers.

Also made it so the mirror job will be skipped on forks.

## Goals and Outstanding Issues
<!--- A clear and concise list of goals (to be) accomplished. --->
- [x] Only allow dispatch to run on `westpa2` branch.
- [x] Allow manual rerun of build and test CI
- [x] restructure build/upload workflows

## Major files changed
<!--- Manually list files or include a diff link in the form of: https://github.com/user/westpa/compare/<initial SHA>..<final SHA> --->
- [x] .github/workflows/mirror.yaml
- [x] .github/workflows/build.yaml
- [x] .github/workflows/test.yaml

## Status
<!--- Delete bullet points that are not relevant. --->
- [x] New feature (non-breaking change which adds functionality)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [x] All new and existing tests passed.

## Additional context
<!--- Add any other context or screenshots about the pull request here. --->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b3afe209fcff`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.