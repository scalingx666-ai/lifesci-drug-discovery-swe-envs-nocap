# Issue

**Title:** Update bleed tag via GitHub REST API in continuous-delivery

## Description

This fixes the bleeding-edge release update by replacing the direct force-push of the `bleed` tag with the GitHub REST API.

The full continuous-delivery path was tested on the fork, including updating an existing `bleed` tag, uploading all release assets, and verifying the published checksums and final tag SHA.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `831acde9faf2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.