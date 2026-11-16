# Issue

**Title:** gxy-tool-bot: use github.event.repository.default_branch instead of hardcoded main

## Description

Fixes 'fatal: couldn't find remote ref main' on repos with master as default branch.

FOR CONTRIBUTOR:
* [ ] I have read the [CONTRIBUTING.md](https://github.com/galaxyproject/tools-iuc/blob/master/CONTRIBUTING.md) document and this tool is appropriate for the tools-iuc repo.
* [ ] License permits unrestricted use (educational + commercial)
* [ ] This PR adds a new tool or tool collection
* [ ] This PR updates an existing tool or tool collection
* [ ] This PR does something else (explain below)

There are two labels that allow to ignore specific (false positive) tool linter errors:

* `skip-version-check`: Use it if only a subset of the tools has been updated in a suite.
* `skip-url-check`: Use it if github CI sees 403 errors, but the URLs work.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f6024c52614e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.