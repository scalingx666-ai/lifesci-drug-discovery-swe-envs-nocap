# Issue

**Title:** build/test on python 3.15

## Description

## Issue Number
<!--- Is this pull request related to any outstanding issues? If so, list the issue number. --->


## Describe the changes made
<!--- A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it. -->
Support Python 3.15. Build/test on them

## Goals and Outstanding Issues
<!--- A clear and concise list of goals (to be) accomplished. --->
- [x] Python 3.15 support 
- [x] Fix readthedocs builds

## Major files changed
<!--- Manually list files or include a diff link in the form of: https://github.com/user/westpa/compare/<initial SHA>..<final SHA> --->
- [x] .github/workflows/build.yaml
- [x] .github/workflows/test.yaml
- [x] devtools/conda-envs/test_env_py315.yaml
- [x] doc/doc_env.yaml
- [x] .readthedocs.yml

## Status
<!--- Delete bullet points that are not relevant. --->
- [x] New feature (non-breaking change which adds functionality)
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d36230d92e7a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.