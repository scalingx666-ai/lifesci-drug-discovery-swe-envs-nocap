# Issue

**Title:** In rexgen example: Enabled reactants and products without bonds.

## Description

In dgllife: Enable graphs without edges in WLN.

*Issue #134*

*Description of changes:*
In rexgen example: Enabled reactant and product graphs that have no edges. This required changes in core (USPTO set and WLN model).  

By submitting this pull request, I confirm that you can use, modify, copy, and redistribute this contribution, under the terms of your choice.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `367c79b71261`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.