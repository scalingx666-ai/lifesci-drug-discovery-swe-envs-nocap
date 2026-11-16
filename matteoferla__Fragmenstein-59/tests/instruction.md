# Issue

**Title:** :bug: Fix AttributeFilledMock with pyrosetta submodule imports

## Description

## Summary
- **** — `import pyrosetta.rosetta.core` no longer raises `TypeError: 'AttributeFilledMock' object is not iterable`
- Adds a `MetaPathFinder` that intercepts all `pyrosetta.*` imports when PyRosetta is absent, returning properly configured mock modules
- Replaces deprecated `pkg_resources` with `importlib.resources` in `branding.py` (compatible with setuptools >= 82)
- Bumps `python_requires` to `>=3.9` (3.7 and 3.8 are EOL)

## Test plan
- [x] Verified `import pyrosetta.rosetta.core as prc` works with the mock
- [x] Verified `from fragmenstein import Wictor` succeeds in a fresh venv without PyRosetta
- [x] Verified `branding.divergent_colors` loads correctly with setuptools 82
- [x] Existing test suite passes (failures are pre-existing PyRosetta-absent tests)

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4f2643065134`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.