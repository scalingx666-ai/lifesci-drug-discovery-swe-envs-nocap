# Issue

**Title:** Clean up workflows

## Description

This PR has the following changes:

1. Remove all redundant model prediction workflows since these will go into a cron job for testing the model. 
2. Change the triggers for the base image upload Ersilia docker image to be triggered manually, and on every push to main branch, and as well as after every Ersilia release.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4216d7ebc9d0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.