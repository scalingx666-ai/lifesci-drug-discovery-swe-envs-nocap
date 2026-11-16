# Issue

**Title:** Fix CI/CD: migrate to GitHub Actions, update outdated badges

## Description

## Summary

- Replace dead Travis CI with **GitHub Actions** (tests on Python 3.8/3.9/3.10/3.11)
- Remove dead landscape.io badge
- Fix outdated badges: Python 3.8+, PyPI v0.9.0

## Changes

| File | Change |
|------|--------|
| `.github/workflows/ci.yml` | New GitHub Actions workflow |
| `.travis.yml` | Removed (service shut down 2021) |
| `README.rst` | Updated badges |
| `setup.py` | Updated badges |

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7e37d97e66ae`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.