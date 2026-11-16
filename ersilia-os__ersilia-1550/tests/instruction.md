# Issue

**Title:** Fix/bug wrong input handling

## Description

Thank you for taking your time to contribute to Ersilia, just a few checks before we proceed
- [X] Have you followed the guidelines in our [Contribution Guide](https://github.com/ersilia-os/ersilia/blob/master/CONTRIBUTING.md)
- [X] Have you written new tests for your core changes, as applicable?
- [X] Have you successfully ran tests with your changes locally?

**Description**

This pull request fixes the bug  by modifying the behavior when an invalid input is provided. Currently, when a wrong input (e.g., a misspelled file name) is passed, Ersilia misinterprets it as a SMILES string and creates an output file containing a single row with "UNPROCESSABLE_INPUT". With this fix, if the output data contains exactly one row marked as "UNPROCESSABLE_INPUT", an error is raised and no output file is created.

**Changes to be made**

1. Updated the DataFrame Class in ersilia/io/output.py:

- Added a Helper Method: added the following helper method to check if the DataFrame contains a single row with the "UNPROCESSABLE_INPUT" marker.

- Modified the write Method: In the write method of the `DataFrame class,` I inserted a check at the beginning to detect this condition. If the condition is met,  an `UnprocessableInputError` is raised to prevent the output file from being created.

2. Added Exception Class in `ersilia/utils/exceptions_utils/api_exceptions.p`y:
Added the exception class `UnprocessableInputError` to support this change and ensure it provides a clear error message with troubleshooting hints.

3. Error Handling:

- Catches `UnprocessableInputError `specifically.
- Displays a formatted error message with troubleshooting hints.
- Deletes any partially created output files (if applicable)

**Status**

- The changes have been implemented and tested locally.
- Manual testing via both CLI and API confirms that invalid inputs now trigger the proper error message and prevent output file creation.

**To do**

- Await code review and address any feedback.

Is this pull request related to any open issue? If yes, replace issueID below with the issue ID

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a6b9aaefc52c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.