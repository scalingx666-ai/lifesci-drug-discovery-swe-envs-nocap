# Issue

**Title:** Remove functionality deprecated as of 0.12.0

## Description

Stacked on #392, which this PR is based on. Review that one first; the first commit here is its commit.

Removes the three pieces of functionality whose deprecation timeline has elapsed, with 0.14.0 expected to be released soon. Each was marked for removal "no earlier than v0.13.0".

### Removed

- `qiskit_addon_sqd.configuration_recovery.post_select_by_hamming_weight` (deprecated in 0.12.0), superseded by `postselect_by_hamming_right_and_left`, which returns the postselected bitstring matrix and renormalized probabilities rather than a mask.
- `qiskit_addon_sqd.subsampling.postselect_and_subsample` (deprecated in 0.12.0), superseded by composing `postselect_by_hamming_right_and_left` with `subsample`.
- Passing `avg_occupancies` to `recover_configurations` as a 1D array (deprecated in 0.10.0). It must now be a length-2 tuple, which is the format `solve_fermion` already returns.

The `optimize_orbitals` and `rotate_integrals` deprecations are left in place, since they were only introduced in 0.13.0.

### Tests

Every `test_recover_configurations` subtest was passing `avg_occupancies` as a 1D array and therefore emitting a deprecation warning. These are converted to the length-2 tuple form, with the equivalent values computed through the conversion the removed code performed, so the assertions are unchanged.

`test_postselect_and_subsample` is removed rather than rewritten: each of its subtests duplicates coverage already provided by `test_subsample` and `test_postselect_by_hamming_right_and_left`, including the error paths, whose messages are raised by those two functions. The `setUp` in `test_configuration_recovery.py` is also dropped, as the fixture it defined was used only by the removed test.

Under `-W error::DeprecationWarning`, the two affected test modules produce 17 failing subtests before this change and none after.

### Docs

The removed functions are dropped from the API docs and from the `_inlined_apis` redirect list in `docs/conf.py`, following the precedent of a6ed58e. The `select_open_closed_shell` guide was migrated off `postselect_and_subsample` in #392, so that the fix can be backported on its own.

Release notes refer to the removed functions with literal markup rather than `:func:` roles, since the targets no longer exist.

<hr>

This pull request was drafted by Claude Opus 5 under my guidance.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0cd51110949e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.