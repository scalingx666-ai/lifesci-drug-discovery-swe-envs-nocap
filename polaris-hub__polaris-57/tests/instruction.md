# Issue

**Title:** fix: Use the Parquet file size and checksum for the table content metadata when creating a dataset on the Hub

## Description

# Changelogs

This PR updates the file size and checksum set as metadata on a dataset's table content to use the Parquet file's attributes. This will let the Hub correctly check the size of the uploaded file and
set the state of the dataset to **ready**.

# Links

-

---

_Checklist:_

- [X] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- ~[ ] _Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._~
- ~[ ] _Update the API documentation if a new function is added, or an existing one is deleted._~
- [X] _Write concise and explanatory changelogs above._
- [X] _If possible, assign one of the following labels to the PR: `feature`, `fix` or `test` (or ask a maintainer to do it for you)._

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `79c844c9bdec`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.