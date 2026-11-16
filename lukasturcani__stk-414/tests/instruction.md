# Issue

**Title:** init_from_rdkit_mol Docstring Edit

## Description

Related Issues: #396

Requested Reviewers: @lukasturcani 

Added additional notes section in the docstring to explain that users should kekulize their molecule prior to calling the `init_form_rdkit_mol` method. It also explains the consequences of not doing so (bond orders changed to 1).
Also fixed a capital letter. 

As this does not change any code, there will be no issues with this code change.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a8311fa6110a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.