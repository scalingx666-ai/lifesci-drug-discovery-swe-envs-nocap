# Issue

**Title:** bump kraken_ocr: update TOOL_VERSION to 7.1.1 and remove environment variable TORCHINDUCTOR_CACHE_DIR

## Description

Recently another [kraken (OCR)](https://pypi.org/project/kraken/) version has been released.
The corresponding conda-forge package has already been built: 

For reviewers:
-  This PR includes next to the kraken-ocr version bump the removal of the environment variable TORCHINDUCTOR_CACHE_DIR as already started here:  but not yet merged.
- All tests are passing locally. 9 tests are erroring out locally with `AssertionError: Staging failed: {"err_msg":"Requested extension 'mlmodel' unknown, cannot upload dataset.","err_code":400008}`
since the in the CI used galaxy version does not include these new datatypes yet. 

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `48d8cfdadc20`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.