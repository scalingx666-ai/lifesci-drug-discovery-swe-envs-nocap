# Issue

**Title:** Bump to 1.1.3: remove pkg_resources, fix numpy 2.x compat

## Description

## Summary
- **Version bump** to 1.1.3 (from 1.1.1 in source; PyPI has 1.1.2)
- **Remove `pkg_resources`** — replaced with `importlib.metadata` and `importlib.resources.files()` API throughout (version.py, demo/_base_dataset_holder.py, issue template)
- **Fix numpy 2.x crash** in `_collapse_ring.py` where `np.where()` returns a 2-D array (`[0]` → `[0][0]`)
- **Normalise SMILES round-trip** in monster_combine test to avoid aromaticity perception mismatches

Cherry-picked selectively from #56 (`pkg_resources-removal`), deliberately excluding changes that would revert the #58 mock-fails fix.

## Test plan
- [x] `python3 -c "from fragmenstein.version import __version__; assert __version__ == '1.1.3'"`
- [x] `python3 -c "from fragmenstein.branding import divergent_colors; print(len(divergent_colors))"`
- [x] `python3 -c "from fragmenstein.version import get_versions"`
- [x] `python3 -m unittest tests.test_mock -v` — all 3 regression tests pass

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0c68d90d43b2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.