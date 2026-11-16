# Issue

**Title:** Add convenience function for downloading a project attachment

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->
In QCPortal, adds a function to the Project model to download an attachment to mirror the Dataset model functionality. It was always possible before to go through the `attachments` property, but this can make it a little easier.

Also modified the dataset download_attachment function to not overwrite by default (to make it a little safer to use)

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2d0b0420aa6b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.