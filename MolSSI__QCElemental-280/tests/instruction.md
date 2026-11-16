# Issue

**Title:** collect qcschema samples

## Description

## Description
People often like to see examples of QCSchema. The qcel test suite already caters to this by writing selected model instances to files. This PR publishes those files to a branch so they can be browsed: https://github.com/MolSSI/QCElemental/tree/qcschema-examples . At some point, we may want to filter out the provenance.version so that every file doesn't change every time.

@bennybp has verbally approved this PR.

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `44fa853d5621`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.