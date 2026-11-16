# Issue

**Title:** Update URL of setup-miniconda action

## Description

See  for context. The developer of the action moved it from personal ownership to an organization and we found that the redirect was not automatically happening at the API level (whereas it was fine with HTTP). A GitHub employee claims the API redirection has been fixed, and the original developer also forked it back as a stopgap, but we should update this for its current home nonetheless.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9e3f5b251f6e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.