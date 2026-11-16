# Issue

**Title:** Fix Floating Point Tolerance in Validations

## Description

Validations used e.g. in measurement addition were not respecting inaccuracies arising from floating point represnetation and or de/serialization, e.g. via json parsers.

- `is_in` checks of numerical parameters now respects a tolerance, embodied by `np.isclose` checks rather than `==`
- A test on campaign level was added

**Note**
I also tried with `math.isclose`, but that gives unreasonable results so I went with numpy. Example: `math.isclose(0.0, -5e-324)` is `False` oO

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1eb9b991632d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.