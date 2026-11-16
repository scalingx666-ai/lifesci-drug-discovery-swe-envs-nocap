# Issue

**Title:** Fix/incorrect header mapping

## Description

Thank you for taking your time to contribute to Ersilia, just a few checks before we proceed
- [X] Have you followed the guidelines in our [Contribution Guide](https://github.com/ersilia-os/ersilia/blob/master/CONTRIBUTING.md)
- [X] Have you written new tests for your core changes, as applicable?
- [X] Have you successfully ran tests with your changes locally?

**Description**

This PR addresses an issue with the header mapping in the standard runner. Previously, the code was using a combined list of predefined example files (`PREDEFINED_EXAMPLE_FILES`), which led to using input files (such as `input.csv`) for header determination. This resulted in incorrect header mapping in `output.csv`.
**Changes  made**

- Split Example Files:

In `ersilia/default.py`, split `PREDEFINED_EXAMPLE_FILES` into two separate lists:

`PREDEFINED_EXAMPLE_INPUT_FILES` (for input files)
`PREDEFINED_EXAMPLE_OUTPUT_FILES` (for output files)

- Update Header Determination:

In `ersilia/serve/standard_api.py`, update the logic to iterate over `PREDEFINED_EXAMPLE_OUTPUT_FILES` (instead of the combined list) when determining the header for CSV output.

`Backward Compatibility:`
 defined PREDEFINED_EXAMPLE_FILES as a concatenation of the input and output lists to ensure that other parts of the code importing the old variable do not break immediately. This can be refactored later once all references are updated.
**Status**

Updated `ersilia/default.py` to include `PREDEFINED_EXAMPLE_INPUT_FILES` and `PREDEFINED_EXAMPLE_OUTPUT_FILES` lists.
Modified` ersilia/serve/standard_api.py` to use the output examples for header determination.
Verified changes locally by running relevant commands for fetching and running the model.
All local tests have passed.
**To do**

Update any additional modules that reference `PREDEFINED_EXAMPLE_FILES` to use the appropriate split variables (`PREDEFINED_EXAMPLE_INPUT` or `PREDEFINED_EXAMPLE_OUTPUT`)

Is this pull request related to any open issue? If yes, replace issueID below with the issue ID

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f1b96d54cab2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.