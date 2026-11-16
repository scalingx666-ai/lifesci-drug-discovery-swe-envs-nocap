# Issue

**Title:** Change recommended by AZ about invalid SMILES in interpolation & sampling results.

## Description

This change will remove all invalid smiles from result table and displays the
number of invalid SMILES in a message about the result table.

Other changes includes:
 - Increase font size of the texts in the table
 - Uniform spacing between components
 - Minor optimation of decorator code.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a86ed80cf47d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.