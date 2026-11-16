# Issue

**Title:** Modernize molplotly: pyproject.toml, drop JupyterDash

## Description

## Summary
- **Migrate from setup.py to pyproject.toml** for modern Python packaging (PEP 621)
- **Replace deprecated JupyterDash** with standard Dash, which now natively supports Jupyter
- **Expand test coverage** with comprehensive tests for `add_molecules` including edge cases, error handling, and SVG rendering
- **Update CI workflow** to use the modernized package setup
- **Add PLAN.md** documenting cleanup and modernization roadmap

## Test plan
- [ ] Verify `pip install .` works with the new `pyproject.toml`
- [ ] Run `pytest tests/` to confirm all tests pass
- [ ] Test `add_molecules` in a Jupyter notebook to verify Dash integration
- [ ] Check that the GitHub Actions CI workflow passes

https://claude.ai/code/session_0117V87rftVNjK2yCo3xZK63

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bc10cb3c4f1f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.