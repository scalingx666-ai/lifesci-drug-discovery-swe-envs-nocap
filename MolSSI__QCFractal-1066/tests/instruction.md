# Issue

**Title:** Web app: Add dataset specification descriptions (and allow editing)

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->
Specifications in datasets can have descriptions.  So we should show them in the specifications table, and also allow for them to be edited in the web app.

This moves the delete/modify actions to the far right, and the modify action brings up the dialog to edit both the name and the description. The description can be long, so it needed the dialog box.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3c95781a63fa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.