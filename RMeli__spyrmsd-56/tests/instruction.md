# Issue

**Title:** Support reading compressed (.gz) files

## Description

## Description

Support reading compressed (.gz) files. Open Babel support `.gz` files natively, therefore only the `utils.molformat()` needed to be fixed (). For RDKit, support is a bit messy since the `gzip` module is needed and SDF files needed to be treated differently.

## Checklist

- [x] Tests
- [x] Documentation
- [x] Changelog

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `00207e3b316d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.