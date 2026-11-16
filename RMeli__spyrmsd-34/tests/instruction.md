# Issue

**Title:** Publication and Minor Improvements

## Description

Add citation to [spyrmsd: symmetry-corrected RMSD calculations in Python](https://jcheminf.biomedcentral.com/articles/10.1186/s13321-020-00455-2) and improve error message when graphs are not isomorphic.

Additionally: fix release badge version, improve README, fix link to documentation on PyPI and generalize `test_rmsd_hungarian_benzene_shifted_rotated`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `09b72110cb05`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.