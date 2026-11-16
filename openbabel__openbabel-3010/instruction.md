# Issue

**Title:** Fix crash from large SD file due to recursion in graphsym

## Description

Replaced unbounded recursion with a single bounded loop (should be one round per atom)

Added regression test based on provided file

## Summary by Sourcery

Prevent large and malformed molecular inputs from crashing graph symmetry and 2D layout processing.

Bug Fixes:
- Prevent graph symmetry refinement from exhausting the call stack on large, non-convergent molecular graphs.
- Prevent 2D layout generation from producing invalid coordinates or reading beyond truncated cycle data.

Enhancements:
- Bound graph symmetry refinement by fragment size while preserving early termination when classes stabilize.

Tests:
- Add regression coverage for non-convergent graph symmetry refinement and truncated-cycle layout failures.

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->

## Summary by CodeRabbit

* **Bug Fixes**
  * Improved graph-symmetry processing to complete reliably for complex structures.
  * Prevented potential hangs and stack exhaustion during symmetry refinement.

* **Tests**
  * Added regression coverage for a large, challenging molecular structure.
  * Expanded the fuzz regression test suite with an additional test case.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b3c041ad759b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.