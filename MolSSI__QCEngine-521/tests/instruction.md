# Issue

**Title:** Fix gctc-gcp gradient for 2.4.0 release

## Description

<!-- Thank you for your contribution! -->

## Description
See changelog. Fixes gcp-correction harness. Checked that the fix heals gcp tests in psi4. CI coverage hits both longstanding 2.3.2 and new 2.4.0 versions.

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ceb9378d1b9a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.