# Issue

**Title:** Handle BentoML errors & clean up failed models

## Description

Thank you for taking your time to contribute to Ersilia, just a few checks before we proceed
- [X] Have you followed the guidelines in our [Contribution Guide](https://github.com/ersilia-os/ersilia/blob/master/CONTRIBUTING.md)
- [X] Have you written new tests for your core changes, as applicable?
- [ ] Have you successfully ran tests with your changes locally?

**Description**

This PR resolves an issue where the Ersilia CLI fails to fetch a model (especially due to BentoML-related errors) but still adds it to the catalog, leaving users unaware of the failed fetch.

**Changes made**

1. Encapsulated BentoML-related errors:

- Wrapped all BentoML subprocess calls in a general BentoMLError to ensure proper error handling downstream.

2. Cleaned up failed model artifacts:

- Implemented logic to remove model artifacts when fetching fails, similar to how artifacts are removed for StandardModelExampleError.

3. Provided user feedback on failures:

- Improved logging and added user prompts to notify them when a model cannot be fetched.
- If a fetch fails, users are asked whether they want to delete the model artifacts and default answer is yes.

**To do**

Relevant tests to ensure the new error-handling mechanism works as expected.

Is this pull request related to any open issue? If yes, replace issueID below with the issue ID

Fix #1505

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e667e2027f5a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.