# Issue

**Title:** gxy-tool-bot: sync workflows to 0.2.1 templates

## Description

- pin gxy-tool-bot==0.2.1 (was 0.2.0)
- on-tool-request: also trigger planning when tool-request/tool-update labels are applied to an existing issue (not just at open)
- on-pr-review: support fork PRs (checkout refs/pull/N/head)
- on-pr-feedback / on-pr-review: derive tool dir from changed files under tools/ when PR title and .tool-name don't resolve

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `19a59bad8913`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.