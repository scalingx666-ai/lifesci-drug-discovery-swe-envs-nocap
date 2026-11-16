# Issue

**Title:** Better error message when RDKit or OpenBabel are not installed

## Description

## Description

When using `spyrmsd` as a standalone tool, RDKit or OpenBabel need to be manually installed, since they are optional dependencies (if `spyrmsd` is used as a library).

This PR adds an error message if neither OpenBabel nor RDKit can be imported. Close #79 and close #80.

## Checklist

- [x] Documentation
- [x] Changelog

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3a510c84b2eb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.