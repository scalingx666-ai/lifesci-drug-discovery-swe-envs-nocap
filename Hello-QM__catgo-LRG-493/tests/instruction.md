# Issue

**Title:** chore(release): v1.4.5

## Description

Release bump to **v1.4.5** + README install docs.

- Bumps desktop app version (package.json, tauri.conf.json, Cargo.toml, Cargo.lock) 1.4.4 → 1.4.5.
- Bumps pip package (server/pyproject.toml) 0.1.0 → 0.1.1 so PyPI accepts the new wheel.
- README (en + zh): document `pip` / `uv` / `mamba` install of the `catgo` package.

Tag `v1.4.5` after merge triggers the desktop / mobile / vsix / hpc asset builds; the release Description is set post-build.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fa44ce06de2f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.