# Issue

**Title:** Corrections for extended molfile support and rdfilereader support of bare rxn files

## Description

- error correction in V3000 parser routine (products and reactants were not correctly separated)
- passing rxn files to rdfilereader led to receiving :nothing on the first iteration, this is now taken care of

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a0cc2ff9297b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.