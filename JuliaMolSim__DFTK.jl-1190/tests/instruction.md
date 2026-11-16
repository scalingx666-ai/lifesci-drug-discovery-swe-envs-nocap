# Issue

**Title:** Fix occupation masks and add tests

## Description

Fixes the issue raised by @antoine-levitt in #1189.

A new test item was also added to `/test/occupation.jl`, checking the sanity of occupation masks over various smearing methods and temperatures.

An additional test specifically designed to fail with the current state of DFTK was added as well.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `908e3c8c38ff`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.