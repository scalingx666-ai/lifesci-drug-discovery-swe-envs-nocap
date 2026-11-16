# Issue

**Title:** Codata2018

## Description

<!-- Thank you for your contribution! -->

## Description
Add the latest physconst dataset

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->

## TODO
- [ ] testing
- [ ] `qcel.constants` stays as 2014 for a good while, I think. For projects that explicitly want to choose 14 or 18, is the idea to build a `myconstants = qcel.PhysicalConstantsContext("CODATA2014")` and use that rather than `qcel.constants`?

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `178e97b384c6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.