# Issue

**Title:** fix: handle mp-api serialising the nested structure field to a dict

## Description

Found while verifying JOSS reviewer issues #642/#643 were fully resolved: running `structure_prediction.ipynb` fresh (real MP API key, current PyPI `mp-api`) crashes at `SmactStructure.from_mp()` with `AssertionError`, unrelated to either issue.

## Root cause

`from_mp()` calls mp-api with `use_document_model=False`, which only controls the *top-level* document type. Whether the nested `"structure"` field comes back as a `Structure` object or an MSONable dict (`@class`/`@module`/`lattice`/`sites`) has changed between mp-api releases — confirmed live against the real API:
- `mp-api==0.45.5` (this repo's `uv.lock` pin) → `Structure` object
- `mp-api==0.46.5` (what a fresh `pip`/`uv` install actually resolves today — installing the packaged wheel doesn't consult this repo's lockfile) → raw dict

The old code asserted the field was already a `Structure` and crashed on the newer mp-api.

## Fix

Convert via `Structure.from_dict()` when the field is a dict, before the existing assert.

## Testing

- Fixed `test_from_mp_mocked_new_api`'s mock, which returned a bare `Structure` and never actually exercised the `isinstance(first, dict)` branch it was meant to cover.
- Added `test_from_mp_mocked_new_api_dict_structure` for the dict-serialised case that was actually crashing.
- All 10 `from_mp`-related tests pass.
- Verified end-to-end against the real Materials Project API with `mp-api==0.46.5` installed: the exact call that previously raised `AssertionError` now returns a correct `SmactStructure` with the right composition.

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->
## Summary by CodeRabbit

- **Bug Fixes**
  - Improved compatibility when retrieving structures from different Materials Project API response formats.
  - Structure data provided as a serialised dictionary is now correctly converted for use alongside legacy structure objects.
  - Improved tutorial compatibility with both dictionary-based and document-based search results.

- **Tests**
  - Added coverage for both supported Materials Project structure response formats.

- **Documentation**
  - Clarified how different API response types should be accessed in the structure prediction tutorial.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5052a83f9a47`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.