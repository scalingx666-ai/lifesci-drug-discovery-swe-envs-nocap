# Issue

**Title:** [WIP] Add support for GitHub actions

## Description

This PR adds preconfigured support for GitHub Actions, following conversation in #90.

# To do

- [X] Parameterize existing implementation in `openkinome/kinoml`
- [x] Add support for Windows
- [x] Add support for non-conda builds
- [x] Apparently [Miniconda is preinstalled in all environments](https://help.github.com/en/actions/automating-your-workflow-with-github-actions/software-installed-on-github-hosted-runners), the location being available at `$CONDA`. Test this is true and functional.
- [x] Variables in GH Actions use some sort of Jinja-syntax (`${{ variable }}`) that interferes with cookiecutter's Jinja processing. I think we just need to escape this on the unprocessed YAML to make the tests pass.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b78f57aa2648`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.