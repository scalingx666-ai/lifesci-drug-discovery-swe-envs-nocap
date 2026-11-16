# Issue

**Title:** moved numba jits to molecule.util. minor updates to other stuff

## Description

Speeds up htmd.molecule.molecule import although it slows down htmd.molecule.util import. Whatever. Some other minor fixes as well

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `330655f6d03a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.