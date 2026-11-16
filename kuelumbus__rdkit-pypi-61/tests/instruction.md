# Issue

**Title:** `uncaught_exceptions` missing in MacOS C++17

## Description

RDKit now compiles with the C++17 standard ().  MacOS has not fully implemented this standard. `uncaught_exceptions` is not available in `libc++.dylib` for some versions.  

Defining `CATCH_CONFIG_NO_CPP17_UNCAUGHT_EXCEPTIONS` for MacOS builds instructs Catch to use a different implementation.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e65b0be4a5fd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.