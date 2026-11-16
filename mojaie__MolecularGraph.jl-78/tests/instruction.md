# Issue

**Title:** Delete Manifest.toml

## Description

Deletes Manifest.toml and adds it to the .gitignore (reduces need to `Pkg.resolve`, especially in Pluto notebooks)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `00c880e6b11b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.