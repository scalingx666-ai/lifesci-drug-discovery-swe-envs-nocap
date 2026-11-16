# Issue

**Title:** be more verbose when failing in the Java Aromatic test

## Description

There's an intermittent (and impossible for me to reproduce) java test failure that happens in CI. This has been going on for years, but it's now starting to become more irritating as the number of CI runs we are doing goes up.

This PR adds additional output to the java test AromaticTests.java in the hopes that collecting a bit more information will help track down what's going on.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c694f9375cf8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.