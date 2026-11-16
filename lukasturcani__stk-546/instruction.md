# Issue

**Title:** Add an internal reaction topology graph

## Description

Related Issues:
Requested Reviewers: @lukasturcani
*Note for Reviewers: If you accept the review request add a :+1: to this post*

Results from `$ uv run coordinate_check tests/ coordinate_outputs`:
Average RMSD: 0
Structures with significant RMSDs: None

This graph allows for internal or intramolecular reactions. Other than some simple fixes, this just adds the necessary class and tests.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `92b3b38e89b6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.