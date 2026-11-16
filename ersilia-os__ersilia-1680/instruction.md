# Issue

**Title:** update base information with dockerhub

## Description

This pull request updates the `dockerhub` method in `ersilia/hub/content/base_information.py` to handle cases where the `new_dockerhub_url` is `None`, `"none"`, or `"null"` by setting the `_dockerhub` attribute to `None`.

Key change:

* Updated the `dockerhub` method to check if `new_dockerhub_url` is `None`, `"none"`, or `"null"`, and set the `_dockerhub` attribute to `None` in these cases. This ensures better handling of null-like values for the DockerHub URL.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e7fa35d5fd58`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.