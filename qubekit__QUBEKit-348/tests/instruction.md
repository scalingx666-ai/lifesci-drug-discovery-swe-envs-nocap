# Issue

**Title:** Old PCMsolver overwrite the pyparsing package

## Description

Matplotlib complains about pyparsing having the wrong version: "ImportError: Matplotlib requires pyparsing>=2.0.1"; you have 1.5.0. Pyparsing package has the right version, but there is a file pyparsing.py in the conda/bin which belongs to the pcmsolver=1.1.4 from the psi4 channel. The new one pcmsolver-1.2.1 resolves this issue.


## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3b0fdbeef497`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.