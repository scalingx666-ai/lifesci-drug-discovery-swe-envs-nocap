# Issue

**Title:** chore(pip): align catgo package version to 1.4.5

## Description

Bumps the pip package (`server/pyproject.toml`) from its legacy 0.1.x line to **1.4.5**, matching the desktop app / release version so `pip install catgo` and the GitHub release share one number.

After merge, dispatch `pypi-publish.yml` to publish catgo 1.4.5 to PyPI.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `83f08e18a466`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.