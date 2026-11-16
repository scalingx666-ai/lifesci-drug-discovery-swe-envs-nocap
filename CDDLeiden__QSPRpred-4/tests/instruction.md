# Issue

**Title:** fix papyrus_class.py to read protein set with correct source_path

## Description

Fixes the issue from the latest `dev` pipeline: https://github.com/CDDLeiden/QSPRpred/actions/runs/7447768072

There was no custom `source_path` defined when calling the method `papyrus_scripts.read_protein_set()`  within `qsprpred/data/sources/papyrus/papyrus_class.py

These changes solve the issue. The only reason the pipeline didn't fully pass is because I had defined a timeout of 2 hours for the pipeline. I didn't know it was taking longer than that but will update it in `dev` after merging this PR.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0d4c4988f3e4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.