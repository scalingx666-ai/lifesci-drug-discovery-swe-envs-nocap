# Issue

**Title:** Add error correction harness

## Description

## Description
Adds a revised error correction harness, as discussed in #210.

The new version of the error correction harness works by catching special exceptions and then updating the "keywords" 
of an AtomicInput to attempt to correct for the error.

To make this happen, I have created as special exception class, a Harness with logic to handle the exception class, and made an example with NWChem

## Changelog description
Implemented the ability for harness to autocorrect common errors

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5a70317eca18`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.