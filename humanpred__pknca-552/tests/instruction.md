# Issue

**Title:** docs: add User Guide navbar link to pkgdown site

## Description

Link the pkgdown function-reference site to the new Quarto user-guide book at https://humanpred.github.io/pknca-book/ via a navbar entry (layer 2 of the three-layer docs structure). Also upgrade the site `url` from http to https, which github.io requires.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `10457993ece0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.