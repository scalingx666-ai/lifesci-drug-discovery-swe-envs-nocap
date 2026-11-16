# Issue

**Title:** Chargemol and ModSem fix

## Description

## Description
This PR fixes v-site fitting with chargemol by using the reorientated coordinates extracted from chargemol when fitting the v-sites. The modified seminario method scaling is also fixed as this was applying the same scaling to all angles.



## Status
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f253a5e0d8e4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.