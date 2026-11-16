# Issue

**Title:** Improved graph, isomorphism and bond rearrangement detection algorithm

## Description

1. Improves the graph generation for metal complexes
2. Graph isomorphism based bond rearrangement can be detected for any arbitrary number of bond rearrangements
3. Faster graph isomorphism check through eigenvalues of Laplacian matrix
4. Adds code to write mol file from a Species object based on the graph


***

## Checklist

* [x] The changes include an associated explanation of how/why
* [x] Test pass
* [x] Documentation has been updated
* [x] Changelog has been updated

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `818b930d263a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.