# Issue

**Title:** Added NWChem to the canonical harness tests, fixed issues

## Description

## Description
NWChem does not pass the standard harness tests. This PR adds it to the suite of harnesses being tested to show it fails, and then fixes an issue around "extra" tags being eaten.

## Changelog description
Fixed missing extras tags in NWChem harness

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6654c74b8373`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.