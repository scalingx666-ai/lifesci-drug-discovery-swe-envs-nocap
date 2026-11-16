# Issue

**Title:** [kraken _segment/_ocr] improve help texts and add citations of the on galaxy EU provided models

## Description

The changes below are based on the initial feedback of @Sch-Da 
- Point to Zenodo and Kraken's model catalog in the model selection help and each tool help
~- Add to the help section the supported model formats~
~- Add segmentation/ocr models citations of the models provided on Galaxy EU~

FOR CONTRIBUTOR:
* [x] I have read the [CONTRIBUTING.md](https://github.com/galaxyproject/tools-iuc/blob/master/CONTRIBUTING.md) document and this tool is appropriate for the tools-iuc repo.
* [x] License permits unrestricted use (educational + commercial)
* [ ] This PR adds a new tool or tool collection
* [x] This PR updates an existing tool or tool collection
* [ ] This PR does something else (explain below)

There are two labels that allow to ignore specific (false positive) tool linter errors:

* `skip-version-check`: Use it if only a subset of the tools has been updated in a suite.
* `skip-url-check`: Use it if github CI sees 403 errors, but the URLs work.

Notes for reviewers:
All tests pass locally, they fail in GitHub CI due to the new datatypes added recently to the branch release_26.1  I expect all tests to pass here as soon the GitHub CI is no longer using Galaxy 26.0.1 (?) for testing.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3f5c0515737c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.