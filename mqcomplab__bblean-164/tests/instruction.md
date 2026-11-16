# Issue

**Title:** Best practices paper

## Description

Notebooks to replicate the BitBirch practices paper where added.
All the new notebooks, necessary data, and functions used are in the best_practices directory in examples.

Modifications to bb_lean module:
- fingerprints.py (new types of fingerprints added)
- similarity.py (estimate_jt_std now samples a random million molecules to do the calculation in case the database is larger than 1 million)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f1f919c1edc0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.