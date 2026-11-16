# Issue

**Title:** added exceptions for null publication and source code

## Description

This pull request updates the `publication` and `source_code` setter methods in `ersilia/hub/content/base_information.py` to handle `None`, `"none"`, and `"null"` values more gracefully by setting the respective attributes to `None`. This improves the robustness of the code when dealing with invalid or null-like input.

### Handling of null-like values:

* `ersilia/hub/content/base_information.py` (`publication` method): Added checks to set `_publication` to `None` if `new_publication` is `None`, `"none"`, or `"null"`.
* `ersilia/hub/content/base_information.py` (`source_code` method): Added checks to set `_source_code` to `None` if `new_source_code` is `None`, `"none"`, or `"null"`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9975d5fa0f74`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.