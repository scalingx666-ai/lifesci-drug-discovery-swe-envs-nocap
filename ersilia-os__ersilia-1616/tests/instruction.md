# Issue

**Title:** Tracking for splunk

## Description

This pull request introduces significant changes to the tracking functionality in the `ersilia` package, including refactoring how tracking is handled, adding new exception handling, and updating the CLI to reflect these changes. The key updates include removing redundant tracking parameters from various methods, centralizing tracking logic within `model.py`, and improving error handling for unsupported tracking scenarios.

### Refactoring and Simplification of Tracking Logic:
* Removed redundant tracking parameters (`track_runs`, `track_run`) from the `run` and `serve` methods in `ersilia/cli/commands/run.py` and `ersilia/cli/commands/serve.py`. Tracking is now managed internally in the `Model` class. [[1]](diffhunk://#diff-a4b14323f1de6ed47571089c0bc8b1f24b290ae419510c9726910ff1db735974L51) [[2]](diffhunk://#diff-a4b14323f1de6ed47571089c0bc8b1f24b290ae419510c9726910ff1db735974L66-R67) [[3]](diffhunk://#diff-bf2cb8d9ea55f818ef68bbb4c3ca35ea81e63f952c2277ca47eefd60b3b08b0eL75-R82) [[4]](diffhunk://#diff-bf2cb8d9ea55f818ef68bbb4c3ca35ea81e63f952c2277ca47eefd60b3b08b0eR93-R98)
* Consolidated tracking initialization logic in `ersilia/core/model.py` within the `serve` and `run` methods. Tracking is now enabled based on session configurations and validated for compatibility (e.g., Dockerized models and CSV outputs). [[1]](diffhunk://#diff-f11c37b66cae27db19f6186c3c81be9de6e57ef05e4f47be27449806d435290aL669-R681) [[2]](diffhunk://#diff-f11c37b66cae27db19f6186c3c81be9de6e57ef05e4f47be27449806d435290aL767-R795) [[3]](diffhunk://#diff-f11c37b66cae27db19f6186c3c81be9de6e57ef05e4f47be27449806d435290aL798-R825)

### Improved Error Handling:
* Introduced a new `TrackingNotSupportedError` exception to handle unsupported tracking scenarios, such as non-Dockerized models or invalid input/output formats. [[1]](diffhunk://#diff-f11c37b66cae27db19f6186c3c81be9de6e57ef05e4f47be27449806d435290aR34-R35) [[2]](diffhunk://#diff-f11c37b66cae27db19f6186c3c81be9de6e57ef05e4f47be27449806d435290aL767-R795) [[3]](diffhunk://#diff-df63a4a9057a3dbbb46b12d386951d02e672d597bf3614cfb670650729a2c6e2R1-R23)
* Added a `throw_ersilia_exception` decorator to improve error reporting in methods like `serve` and `run`. [[1]](diffhunk://#diff-f11c37b66cae27db19f6186c3c81be9de6e57ef05e4f47be27449806d435290aL669-R681) [[2]](diffhunk://#diff-f11c37b66cae27db19f6186c3c81be9de6e57ef05e4f47be27449806d435290aR750-L750)

### Updates to CLI Output:
* Enhanced CLI output in `serve.py` to provide clearer feedback on session directories, tracking status, and other runtime details. Updated messages and icons for better user experience. [[1]](diffhunk://#diff-bf2cb8d9ea55f818ef68bbb4c3ca35ea81e63f952c2277ca47eefd60b3b08b0eR93-R98) [[2]](diffhunk://#diff-bf2cb8d9ea55f818ef68bbb4c3ca35ea81e63f952c2277ca47eefd60b3b08b0eL111-R120)

### Code Cleanup:
* Removed unused imports and redundant code in `model.py`, such as the old tracking initialization logic. [[1]](diffhunk://#diff-f11c37b66cae27db19f6186c3c81be9de6e57ef05e4f47be27449806d435290aL10-L11) [[2]](diffhunk://#diff-f11c37b66cae27db19f6186c3c81be9de6e57ef05e4f47be27449806d435290aL200-L216)
* Simplified the `_run` and `run` methods by removing unnecessary parameters and ensuring tracking logic is centralized. [[1]](diffhunk://#diff-f11c37b66cae27db19f6186c3c81be9de6e57ef05e4f47be27449806d435290aL717-R724) [[2]](diffhunk://#diff-f11c37b66cae27db19f6186c3c81be9de6e57ef05e4f47be27449806d435290aL813-R835)

### New Exceptions for Tracking:
* Added `TrackingNotSupportedError` and `NoAWSCredentialsError` to handle specific tracking-related issues, improving robustness and user feedback. Have you written new tests for your core changes, as applicable?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b8db14e10d7a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.