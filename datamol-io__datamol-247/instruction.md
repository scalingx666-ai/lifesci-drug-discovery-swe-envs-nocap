# Issue

**Title:** ci: dependabot action bump + stop version updates

## Description

- Merge the Dependabot GitHub-Actions bump (PR #245: setup-uv v9→v10, codecov-action) into main.
- Remove \`.github/dependabot.yml\` to stop future Dependabot version-update PRs on this repo (security alerts remain a separate repo setting).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3c5d53d9cae1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.