# Issue

**Title:** Plugin charge fix

## Description

## Description
This PR fixes a potential issue where the qubekit plugin used for fitting would set charges to dummy values of 0 for everything if the parameter handlers were resolved with library charges before the plugin handler. This change should mean the correct charges are applied regardless of order. 


## Status
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3338e46ddd37`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.