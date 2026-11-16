# Issue

**Title:** Wire plugin-payload rebuild into the nightly sync workflow

## Description

Adds the `plugin_sync.py --write` rebuild step so nightly sync PRs stay plugin-sync green. Runs on `ubuntu-latest` (no GPU). PR is opened via a GitHub App token — the org blocks the default GITHUB_TOKEN from creating PRs. Requires repo var `SKILL_SYNC_APP_ID` + secret `SKILL_SYNC_APP_PRIVATE_KEY` (App setup in progress).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d64bc5e28ece`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.