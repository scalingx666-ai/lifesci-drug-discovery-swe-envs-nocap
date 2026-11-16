# Issue

**Title:** Handle Link Nodes in CXSMILES (Ring flags now set when reading from SMILES)

## Description

In midst of writing a blog post on repeat groups I realised we don't handle link nodes CXSMILES. Quite east to handle just treated that as Sgroups.

It may be useful to add the optimisation going the other way as well.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7772918f1c69`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.