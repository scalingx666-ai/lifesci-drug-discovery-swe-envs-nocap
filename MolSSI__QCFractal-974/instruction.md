# Issue

**Title:** Handle more file types when uploading molecule files

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

This allows for xyz and json files, and also compressed archives of those files (`.zip`, `.tar.gz`, `.tar.bz2`, `.tar.xz`)

Also improves error handling by returning a list of string errors, and also improves the `allowed_file_extensions` option in `wrap_route`

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0c0b26b11f28`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.