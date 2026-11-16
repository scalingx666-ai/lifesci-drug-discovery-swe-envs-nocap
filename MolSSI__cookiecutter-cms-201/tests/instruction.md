# Issue

**Title:** Remove LGTM add CodeQL

## Description

This PR removes `.lgtm.yml`, which is deprecated and adds a workflow for CodeQL through GitHub Actions. This is the "default" CodeQL workflow that is added to a Python repository at the moment. I obtained it by running the CookieCutter, pushing to GitHub, enabling CodeQL and choosing "Advanced" so that I would get an GHA yaml.

`permissions: read` is also added to the CI workflow to avoid a CodeQL trigger.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `be309dccd0da`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.