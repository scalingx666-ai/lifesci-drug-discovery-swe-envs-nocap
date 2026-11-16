# Issue

**Title:** feat: divide-and-conquer fallback for failing molecules in batch runs

## Description

Thank you for taking your time to contribute to Ersilia, just a few checks before we proceed
- [x] Have you followed the guidelines in our [Contribution Guide](https://github.com/ersilia-os/ersilia/blob/master/CONTRIBUTING.md)
- [ ] Have you written new tests for your core changes, as applicable?
- [x] Have you successfully ran tests with your changes locally?

**Description**

This PR addresses two issues: (1) a crash when running models where one or more molecules in a batch cause the API to error, previously the whole run failed with no output; (2) a `TypeError` crash when serving a model that was fetched from DockerHub and has no local bundle directory.

**Changes to be made**

- Add` _post_batch_with_fallback` to `StandardCSVRunApi`: when a batch POST fails, split it in half and retry each half recursively (divide and conquer). Single molecules that consistently fail are assigned empty output columns in the final CSV rather than aborting the run. Input/output row order is preserved.
- Remove the automatic printing of the full output CSV/JSON content to the terminal after `ersilia run` completes.
- Guard` _get_bundle_location()` returning None in `autoservice.py` and `base.py` so that serving Docker-fetched models  no longer raises a `TypeError`.
- Change `_LocalService.__init__` to set `self.server = None` instead of raising an exception when the pack method is not FastAPI, allowing `is_available()` to be called safely during service class auto-detection.

**Status**
Implemented and tested locally against a Docker-served model with a mixed input containing valid and invalid molecules. The output CSV correctly contains results for all valid molecules and empty columns for failing ones, and the run no longer crashes.

Related to #1839

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0ac10d8e8292`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.