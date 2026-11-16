# Issue

**Title:** Stamp output skeleton with the Cookiecutter Template version

## Description

Adds provenance information to the output project based on the current
version of the CMS cookiecutter template itself (*not* the cookiecutter
program). Right now its a manual update of the version in the
`cookiecutter.json` file, but its better than touching it everywhere by
hand. The way its implemented is undocumented in Cookiecutter itself
and my intuition is its unsafe, but I cannot think of a simpler
solution (xref audreyr/cookiecutter#1135).

This may be the formal solution to #48, but for now, it should be
considered a partial fix.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `79ee84559f45`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.