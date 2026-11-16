# Issue

**Title:** Some testing & other cleanup

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->
Cleans up the testing & pyproject.toml layout, and removes some unused packages and features.

These were done as part of the updgrade to pydantic v2, but are enough for a small PR like this.

* Adds top-level pyproject.toml for common options for black & pytest
* Moves the pytest configuration from the qcarchivetesting package to the top level (helps prevent some warnings)
* Removes ability to upgrade server config from very old versions.
* Updates molecule tests a little (for some future molecule changes) 
* Removes typing extensions dependency (lets see how CI does with this)

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `631ac078feeb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.