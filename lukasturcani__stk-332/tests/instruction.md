# Issue

**Title:** Add Warning for Macrocycle from 2 BBs

## Description

Related Issues: #330
Requested Reviewers: @lukasturcani

This PR introduces an error to let the user know (in a hard way, because the output is nonsense) that alignment is not supported for Macrocycles formed from only 2 building blocks and 1 repeat unit. This is an edge use-case that I think can be fixed, with large rewrites of the Macrocycle class. A 2 building block Macrocycle also makes less sense, then using a different topology for that molecule.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eeb3ae082bf9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.