# Issue

**Title:** [kraken _segment/_ocr] Rename datatable/.loc file, remove code duplication, and fix tests

## Description

After the recent introduction of the kraken_ocr suite ().
@bgruening, @anuprulez, and I found some minor things to improve.

Summary of the changes:
- renamed datatables/.loc file to pretrained_mlmodels_various_sources; 
added new columns for attribution and changed column order
- replace datatable and outputs logic in _segment and _ocr with macros
- added README how to populate the models folders for local testing
- fixed tests so they work with the new datatypes (introduced with: )

FOR CONTRIBUTOR:
* [x] I have read the [CONTRIBUTING.md](https://github.com/galaxyproject/tools-iuc/blob/master/CONTRIBUTING.md) document and this tool is appropriate for the tools-iuc repo.
* [x] License permits unrestricted use (educational + commercial)
* [ ] This PR adds a new tool or tool collection
* [x] This PR updates an existing tool or tool collection
* [ ] This PR does something else (explain below)

There are two labels that allow to ignore specific (false positive) tool linter errors:

* `skip-version-check`: Use it if only a subset of the tools has been updated in a suite.
* `skip-url-check`: Use it if github CI sees 403 errors, but the URLs work.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f115a307fffb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.