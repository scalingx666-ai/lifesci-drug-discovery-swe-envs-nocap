# Issue

**Title:** fix: convert dict-serialised structure in parse_mprest for newer mp-api

## Description

## Summary
- `parse_mprest()` (used by `StructureDB.add_mp_icsd`) passed `data["structure"]` straight into `SmactStructure.from_py_struct()`, which raises `TypeError` unless given a pymatgen `Structure`.
- `mp-api`'s `use_document_model=False` only controls the top-level document; whether the nested `"structure"` field deserialises to a `Structure` or stays an MSONable dict has changed between `mp-api` releases (0.45.5 returns a `Structure`; 0.46.5 — what a fresh `pip install` resolves to today, since `pyproject.toml` only requires `mp-api>=0.45.3` — returns a dict).
- With a dict, every structure failed with `"Couldn't decorate ... with oxidation states"` and `add_mp_icsd` silently returned `0`, which is exactly the symptom reported in #664 when running `docs/tutorials/structure_prediction.ipynb`.
- This is the same class of bug already fixed for `SmactStructure.from_mp()` in 90c194be, but that fix missed this sibling call path in `database.py`. This PR mirrors it there.

## Test plan
- [x] Added `test_parse_mprest_dict_structure`, which reproduces the exact warning from #664 on the old code and passes with the fix.
- [x] Verified against a fresh install that resolves `mp-api==0.46.5` (matching the reporter's environment).
- [x] `pytest smact/tests/test_structure.py` — 69 passed, 1 skipped (live MP API test, no key available).
- [x] `ruff check` / `ruff format --check` on changed files.

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->
## Summary by CodeRabbit

* **Bug Fixes**
  * Improved structure parsing for Materials Project API responses that provide serialised structure data.
  * Ensured these responses are converted correctly and returned as valid SMACT structures.

* **Tests**
  * Added coverage for parsing serialised structure data from newer API responses.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c6dadd4efd8b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.