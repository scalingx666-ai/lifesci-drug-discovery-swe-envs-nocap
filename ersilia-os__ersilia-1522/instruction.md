# Issue

**Title:** Fix: Truncate large debug outputs to prevent terminal clutter and Improve log readability

## Description

Thank you for taking your time to contribute to Ersilia, just a few checks before we proceed
- [X] Have you followed the guidelines in our [Contribution Guide](https://github.com/ersilia-os/ersilia/blob/master/CONTRIBUTING.md)
- [X] Have you written new tests for your core changes, as applicable?
- [X] Have you successfully ran tests with your changes locally?

**Description**

This PR addresses the issue of cluttered terminal logs caused by large array outputs in debug messages. 
- Added truncation to log only the first 10 elements of arrays.
- Includes count of remaining elements for context.

**Changes to be made**

To address the issue of cluttered terminal logs caused by long debug outputs, I have implemented a truncation mechanism in the `__cast_values` method. This change modifies how debug logs handle long lists or arrays by displaying only the first 10 elements and indicating how many additional elements are present. This ensures the logs remain concise and readable.

**Status**

Steps taken:

1. Identified the source of the issue within the` __cast_values` method.
2. Updated the logging logic to:

- Check if the value being logged is a list or has a` __len__ `attribute.
- Display only the first 10 elements, followed by a note on the remaining count.
- Log non-array values as-is for clarity.
3. Tested the changes to verify that truncation works as expected without affecting the functionality.

Is this pull request related to any open issue? If yes, replace issueID below with the issue ID

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d429f07da593`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.