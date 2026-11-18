# Issue

**Title:** Fix Setting Compilation Flags for GitHub CI Workflow Tests

## Description

This PR switches to using the compiler type keywords (GNU, CLANG, etc.) for the build systems in order to automatically set the compiler executables and compilation flags used (and thereby tests the common selections by end users).

The current code does manually set the compiler executables but neglects to set the compilation flags (which is a bug).  This fixes this issue.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `91e509cbf85b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.