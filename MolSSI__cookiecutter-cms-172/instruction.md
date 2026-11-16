# Issue

**Title:** Replacing provision-with-micromamba action with setup-micromamba action.

## Description

This PR is replacing the deprecated [provision-with-micromamba](https://github.com/marketplace/actions/provision-with-micromamba) action with the newer [setup-micromamba](https://github.com/marketplace/actions/setup-micromamba) action.

Updates follow the recommended migration steps from the provision-with-micromamba page.

Actions to update:
- [x] verify-ghas.yaml - conda-forge-dep
- [x] verify-ghas.yaml - conda-defaults-dep
- [x] cookiecutter ci.yaml - test

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `401afa96a3e0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.