# Issue

**Title:** Feat: Add Support for multiple test-set benchmarks

## Description

This pull request introduces support for multiple test sets in the `SplitV2` class and related functionality across the codebase. The changes enhance flexibility by allowing benchmarks to define more than one test set, while maintaining backward compatibility with the previous single-test-set format.

### Enhancements to `SplitV2` functionality:

* Modified the `SplitV2` class to replace the single `test` field with a `test_sets` dictionary, enabling support for multiple test sets. Added validators to ensure proper deserialization, validation, and backward compatibility for single-test-set benchmarks.


### Changes to benchmark specification and client:

* Updated the `BenchmarkV2Paths` class to allow dynamic fields for multiple test sets and added a `test_sets` property for structured access to test set URLs. Maintained backward compatibility with the single `test` field.
* Modified `_get_v2_benchmark` in `polaris/hub/client.py` to handle multiple test sets when parsing split data from the response. Structured test sets separately from the training set.

### Testing improvements:

* Added new test cases in `tests/test_benchmark_v2.py` to validate functionality for multiple test sets, including validation rules, backward compatibility, and split properties.
* Introduced a new pytest fixture `test_benchmark_v2_multiple_test_sets` in `tests/conftest.py` for creating benchmarks with multiple test sets.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `52d3f8d303c5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.