# Issue

**Title:** Add ARM CI and prevent checkpoint leaks

## Description

# Summary

- Add an ARM CI matrix covering `ubuntu-24.04-arm` and `macos-14`.
- Run ARM tests with Python 3.12, PySCF 2.11, and `OMP_NUM_THREADS=4`.
- Add a reusable CPU diagnostics action for architecture-specific CI failures.
- Prevent unused PySCF checkpoint files from being created during tests.
- Remove platform-specific warning suppressions for leaked checkpoint files.

## Background

PySCF creates a `NamedTemporaryFile` for every SCF object, even when checkpointing is not requested. Some transformed SCF objects participate in reference cycles, which can delay file cleanup until cyclic garbage collection.

Python then emits a `ResourceWarning`, which pytest 9 re-emits as a `PytestUnraisableExceptionWarning`. Because warnings are treated as errors, an unrelated test can fail when it happens to trigger garbage collection. The existing suppression only matched Linux `/tmp` paths and did not cover macOS paths under `/var/folders`.

The new session-scoped fixture enables PySCF's `MUTE_CHKFILE` setting during tests and restores its previous value afterward. This prevents the unused files from being opened instead of suppressing their cleanup warnings. Production behavior is unchanged.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `35dd9b91b6b2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.