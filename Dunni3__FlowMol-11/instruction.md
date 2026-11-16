# Issue

**Title:** Sanitize qm9 molecules when processing dataset

## Description

About 1% of the QM9 dataset contains pentavalent carbon, somehow. So training on these compounds degrades model performance on the metrics we measure. Easy fix, remove all molecules from QM9 that cannot be sanitized by rdkit.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ab062935ea20`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.