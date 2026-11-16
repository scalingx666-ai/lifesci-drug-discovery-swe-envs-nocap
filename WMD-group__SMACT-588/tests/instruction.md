# Issue

**Title:** Fix TypeError crash for noble gases with explicit oxidation state sets

## Description

## Summary

- `smact_validity` with an explicit `oxidation_states_set` (e.g. `'smact14'`, `'icsd16'`) raised an unhandled `TypeError` for compositions containing noble gases (He, Ne, Ar, Rn) because their `None` oxidation states were passed directly to `itertools.product`
- The `oxidation_states_set=None` default path already had an element-level guard; this PR adds an equivalent single guard after all explicit-set branches
- Noble gas compounds with known oxidation states (Kr, Xe) continue to work correctly

## Test plan

- [ ] `smact_validity('NeF2', oxidation_states_set='smact14')` returns `False` without crashing
- [ ] `smact_validity('XeF2', oxidation_states_set='icsd24')` still returns `True`
- [ ] All 30 existing tests pass

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->

## Summary by CodeRabbit

## Release Notes

* **Bug Fixes**
  * Enhanced validation to prevent errors when processing compounds with undefined or invalid oxidation states. The system now returns early when oxidation-state data is missing or incomplete, avoiding downstream processing failures.

* **Tests**
  * Added comprehensive test coverage for noble gas validity assessment across multiple oxidation state datasets to ensure correct handling of elements with undefined oxidation states.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5b55663c103a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.