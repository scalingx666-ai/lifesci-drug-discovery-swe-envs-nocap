# Issue

**Title:** Feat/eosvc GitHub fetch

## Description

Thank you for taking your time to contribute to Ersilia, just a few checks before we proceed
- [x] Have you followed the guidelines in our [Contribution Guide](https://github.com/ersilia-os/ersilia/blob/master/CONTRIBUTING.md)
- [ ] Have you written new tests for your core changes, as applicable?
- [x] Have you successfully ran tests with your changes locally?

**Description**

Integrates eosvc as an alternative backend for downloading large model artifacts (checkpoints, fit files) from GitHub, replacing Git LFS for models that include an access.json file. When fetching with --from_github, ersilia now checks for access.json in the repository and, if present, uses eosvc to pull artifacts from S3 instead of relying on Git LFS.

**Changes to be made**

- Added `EosvcRequirement` class in `ersilia/setup/requirements/git.py` to check, install, and ensure eosvc is available in the active Python environment at fetch time.

- Extended `GitHubDownloader` in `ersilia/utils/download.py`with a use_eosvc flag and methods to detect `access.json`, auto-install eosvc, and download `checkpoints/fit` directories via eosvc.cli.

- Updated `ModelRepositoryGetter` in `ersilia/hub/fetch/actions/get.py` to pass `use_eosvc=force_from_github `to `GitHubDownloader`.

- Added eosvc as a dependency in `pyproject.toml`

**Status**

Implementation is complete. The eosvc download path is activated when `--from_github` is passed and` access.json` is present in the fetched repo. Falls back to Git LFS if eosvc cannot be installed.


Related to #1836

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c502f7d0c459`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.