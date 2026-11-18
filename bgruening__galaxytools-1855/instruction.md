# Issue

**Title:** Update 3Dtrees: RayCloudTools v1.2.0

## Description

Updates RayCloudTools, which adds built-in `LAZ` support for `LAZ > 1.2` based on `LASzip` and eliminates the need for the input translation with `pdal`. It further provides a temporary fix for  while the issue is pending.

FOR CONTRIBUTOR:
* [X] I have read the [CONTRIBUTING.md](https://github.com/galaxyproject/tools-iuc/blob/master/CONTRIBUTING.md) document and this tool is appropriate for the tools-iuc repo.
* [X] License permits unrestricted use (educational + commercial)
* [ ] This PR adds a new tool or tool collection
* [X] This PR updates an existing tool or tool collection
* [ ] This PR does something else (explain below)

There are two labels that allow to ignore specific (false positive) tool linter errors:

* `skip-version-check`: Use it if only a subset of the tools has been updated in a suite.
* `skip-url-check`: Use it if github CI sees 403 errors, but the URLs work.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `887d8784ad34`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.