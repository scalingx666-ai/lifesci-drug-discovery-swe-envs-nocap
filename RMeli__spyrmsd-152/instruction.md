# Issue

**Title:** Consolidate package configuration in pyproject.toml

## Description

## Migration Plan: Move to pyproject.toml

This PR migrates all configuration from `setup.cfg` and `setup.py` to `pyproject.toml`, following modern Python packaging standards. This PR also properly merges the latest changes from the `develop` branch.

### Checklist

- [x] Explore repository structure and understand current configuration
- [x] Update `pyproject.toml` with all metadata from `setup.py`
- [x] Migrate tool configurations from `setup.cfg` to `pyproject.toml`
- [x] Migrate coverage configuration from `.coveragerc` to `pyproject.toml`
- [x] Create `.flake8` config file (flake8 doesn't support pyproject.toml)
- [x] Update GitHub workflow files to use `pip install -e .` instead of `setup.py develop`
- [x] Remove `setup.cfg` file
- [x] Remove `setup.py` file
- [x] Remove `.coveragerc` file
- [x] Test that the package can still be installed and built
- [x] Run code review and security checks
- [x] Fix pre-commit formatting issues
- [x] Add platform classifiers
- [x] Properly merge develop branch with actual merge commit
- [x] Add test and dev optional dependencies
- [x] Add parallel optional dependency
- [x] Add requests to test dependencies
- [x] Update CHANGELOG with migration changes

### Summary of Changes

**Files Modified:**
- `pyproject.toml`: Migrated all package metadata and tool configurations
  - Added `[project]` table with metadata from `setup.py`
  - Added `[project.optional-dependencies]` from `setup.py` (openbabel removed per develop branch)
  - Added `parallel` optional dependency: pebble (for parallel execution)
  - Added `test` optional dependencies: pytest, pytest-cov, pytest-benchmark, requests
  - Added `dev` optional dependencies: mypy, types-requests, flake8, black, isort, pre-commit
  - Added platform classifiers (Linux, Mac OS-X, Unix, Windows)
  - Added `[tool.pytest.ini_options]` from `setup.cfg`
  - Added `[tool.coverage.run]` and `[tool.coverage.report]` from `.coveragerc`
  - Added `[tool.mypy]` from `setup.cfg`
  - Added `[tool.isort]` from `setup.cfg`
- `.github/workflows/mypy.yml`: Changed to use `pip install -e .` instead of `python setup.py develop`
- `.github/workflows/flake8.yml`: Changed to use `pip install -e .` instead of `python setup.py develop`
- `tests/test_graph.py`: Fixed black formatting (parenthesized context managers)
- `CHANGELOG.md`: Documented all migration changes
- Properly merged changes from `develop` branch (Open Babel support removal and other updates) with proper merge commit

**Files Added:**
- `.flake8`: Created separate config for flake8 (doesn't support pyproject.toml)

**Files Removed:**
- `setup.cfg`: All configurations migrated to `pyproject.toml` and `.flake8`
- `setup.py`: No longer needed with flit build backend (properly resolved merge conflict)
- `.coveragerc`: Coverage configuration migrated to `pyproject.toml`

**Testing:**
- ✅ Package installs successfully with `pip install -e .`
- ✅ Package builds successfully with `python -m build`
- ✅ All tool configurations working (flake8, mypy, isort, pytest, coverage)
- ✅ All pre-commit checks pass
- ✅ Platform classifiers correctly added
- ✅ Properly merged with develop branch (actual merge commit b6ca06d)
- ✅ Test, dev, and parallel optional dependencies added and verified
- ✅ requests added to test dependencies for test_large.py
- ✅ CHANGELOG updated with migration changes
- ✅ Code review passed
- ✅ Security scan passed

<!-- START COPILOT ORIGINAL PROMPT -->

<details>

<summary>Original prompt</summary>

>
> ----
>
> *This section details on the original issue you should resolve*
>
> <issue_title>Move fully to pyproject.toml</issue_title>
> <issue_description></issue_description>
>
> <agent_instructions>Remove setup.cfg in favor of moving everything to pyproject.toml. setup.py might also be removed/updated.</agent_instructions>
>
> ## Comments on the Issue (you are @copilot in this section)
>
> <comments>
> </comments>
>

</details>

<!-- START COPILOT CODING AGENT SUFFIX -->

- Fixes RMeli/spyrmsd#150

<!-- START COPILOT CODING AGENT TIPS -->
---

💡 You can make Copilot smarter by setting up custom instructions, customizing its development environment and configuring Model Context Protocol (MCP) servers. Learn more [Copilot coding agent tips](https://gh.io/copilot-coding-agent-tips) in the docs.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `db19a30703f3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.