# Issue

**Title:** acknowledge namespace packages

## Description

<!-- Thank you for your contribution! -->

## Description
So this came about because conditional tests were running in psi4 even though the module whose presence was the condition wasn't there. Turned out, `which_import` was detecting a non-python directory (CTest to be exact) with the module name as a namespace module and so activating the test. This PR allows that behavior (mostly for testing purposes) but generally stamps it out.

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `846928c80b68`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.