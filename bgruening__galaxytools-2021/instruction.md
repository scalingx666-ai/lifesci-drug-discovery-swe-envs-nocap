# Issue

**Title:** gxy-tool-bot to 0.2.0

## Description

gets a pr review flow, a tool update user request flow and a smart version autobump flow, plus general improvements to existing flows. i think i set autobump to check every day but not attempt more than 3 tools at a time. let me know if wed rather leave out autobump.

FOR CONTRIBUTOR:
* [x] I have read the [CONTRIBUTING.md](https://github.com/galaxyproject/tools-iuc/blob/master/CONTRIBUTING.md) document and this tool is appropriate for the tools-iuc repo.
* [x] License permits unrestricted use (educational + commercial)
* [ ] This PR adds a new tool or tool collection
* [ ] This PR updates an existing tool or tool collection
* [x] This PR does something else (explain below)

There are two labels that allow to ignore specific (false positive) tool linter errors:

* `skip-version-check`: Use it if only a subset of the tools has been updated in a suite.
* `skip-url-check`: Use it if github CI sees 403 errors, but the URLs work.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4c424386fe82`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.