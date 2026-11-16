# Issue

**Title:** better molecule-from-string error message

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->
See psi4/psi4#2287 . When there's a syntax error in a mol string, and it can't be matched in any format/dtype (psi4, xyz, etc.), presently the last error that gets raised includes the whole molecule string. This isn't helpful when one dtype might have _nearly_ matched it, so now the code stores the shortest error and re-raises that.

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e102d0b1b6de`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.