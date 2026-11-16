# Issue

**Title:** v4.1.1: read the help banner version from the package

## Description

v4.1.0 shipped with `pandadock --help` reporting **Version: 4.0.0**.

The banner in `docking_cli.py` held a hardcoded literal that the release bump did not touch. Package metadata, `pandadock.__version__` and `--version` were all correct, so the defect was confined to the first thing a user sees — but that is enough for someone to conclude their install failed.

```
pip show pandadock       → 4.1.0   ✓
pandadock.__version__    → 4.1.0   ✓
pandadock --help banner  → 4.0.0   ✗
```

It now reads from the package, as the report, metal, tethered and ML banners already do.

### Why the existing test missed it

`test_version_is_single_sourced` compares `__version__` across sub-packages, so it passed: the stale value was prose inside a help string, not a module attribute.

`tests/test_imports.py` now scans every module for a literal `Version: N.N` and fails on it. That also guards the five banners fixed earlier in this cycle.

Version bumped to 4.1.1. 74 tests pass; both artifacts pass `twine check`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6df0a508eb6e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.