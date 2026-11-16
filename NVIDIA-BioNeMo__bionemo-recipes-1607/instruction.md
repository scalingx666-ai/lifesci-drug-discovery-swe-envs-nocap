# Issue

**Title:** chore: configure grouped weekly dependabot updates for all ecosystems

## Description

Adds explicit dependabot configuration for all package ecosystems detected in the repo, using **grouped updates** so each ecosystem/directory produces at most **one PR per week**.

## What this does

- **uv** (`sparse_autoencoders`) — single grouped PR
- **pip** (`codonfm_ptl_te`, `geneformer`) — single grouped PR each
- **npm** (dashboard apps) — single grouped PR each
- Existing **gitsubmodule** and **docker** configs preserved

All new entries use:
- `open-pull-requests-limit: 1`
- `groups: { all-dependencies: { patterns: ["*"] } }` (one PR for all bumps)
- Weekly cadence

## Why

Without explicit config, GitHub's Dependabot security updates create individual PRs per package per directory, which caused the recent flood of 11+ PRs in a few days. With grouped updates, we'll get at most one PR per directory per week regardless of how many advisories fire.

## Note

The security update PRs will still fire for packages NOT covered by this config. If other `requirements.txt` files (esm2_native_te, llama3_native_te, etc.) start getting hit, we can add them here too — but for now only the directories that had active advisories are included.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4e6654303a33`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.