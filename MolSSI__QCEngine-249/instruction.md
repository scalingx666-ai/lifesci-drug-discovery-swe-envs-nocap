# Issue

**Title:** Implement support for xtb API

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->
Add thin wrapper around [`xtb-python`](https://xtb-python.readthedocs.io) project. For the integration into QCEngine this should cover all the changes needed for `xtb` support. The actual harness for `xtb` will be maintained in the `xtb-python` project.

~~Important: `xtb-python` is still work in progress and not yet available on conda-forge!~~

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->
Implement support for the extended tight binding (`xtb`) program package.

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `800f8d6fdb3a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.