# Issue

**Title:** Make AtomValenceTool initialization thread-safe

## Description

## Summary

Replace the lazily initialized mutable valence map in `AtomValenceTool` with a
safely published immutable map initialized during class loading.

The previous implementation assigned the shared map before populating it. A
concurrent first call could therefore observe a non-null but incomplete table
and fail while unboxing a missing value.

## Changes

- construct the complete valence table during class initialization;
- expose the table internally as an immutable map;
- preserve the existing behavior for element symbols not present in the table;
- add a focused unit test that verifies all currently supported symbols return
  a nonzero valence.

This issue was found while porting PaDEL-Descriptor from CDK 1.x to CDK 2.13,
but the change and test are independent of PaDEL.

.

## Testing

- The original standalone concurrent-first-use reproducer was run 20 times
  against the patched class with no failure.
- The supported-element test verifies the public functionality without
  duplicating the implementation's valence values.
- The repository CI should run the complete Maven and code-quality checks.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7ef828bc2e2e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.