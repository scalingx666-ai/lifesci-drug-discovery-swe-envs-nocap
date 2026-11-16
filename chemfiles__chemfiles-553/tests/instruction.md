# Issue

**Title:** Reject non-finite unit cell lengths

## Description

This patch accompanies #552.

`UnitCell` rejected negative lengths but accepted NaN and infinity through both the length-vector and direct matrix constructors, creating cells with non-finite lengths and volumes. The patch validates all length values and all direct matrix entries with `std::isfinite()` before the existing geometry checks, while preserving supported zero-length cells.

Regression coverage includes NaN and ±infinity through both constructors, `set_lengths()`, and valid zero-length controls. Local validation:
- pre-patch C++ reproducer confirmed NaN/∞ acceptance and invalid volumes;
- `cmake --build build --target cell -j2` passed;
- `ctest --test-dir build -R '^cell$' --output-on-failure` passed;
- `git diff --check` passed.

This report and patch were prepared as part of an LLM-assisted testing study of chemistry repositories. The reproducer was run locally and minimized before filing.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `582e6da1ce7c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.