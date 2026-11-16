# Issue

**Title:** Implement support for DFT-D4

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->
- [x] implement harness for `dftd4` Python API (closes )
- [x] Finish upstream implementation (see )
- [x] Publish Python API on conda-forge (see )
- [x] Add a few regression tests
- [x] Add DFT-D4 to tests in this repository (requires cf package, upstream implementation and new `dftd4` release)

*Note:*
The Python API must be explicitly enabled when building `dftd4` or can exist separately from a `dftd4` installation.
The harness can therefore fail to use `dftd4` even if a `dftd4` installation is present, in this case it could have a fallback for a FIFO calculator (xyz + command line input, JSON dump output), but this is work for a different PR.

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->
Implement support for DFT-D4

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7ac0f546195b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.