# Issue

**Title:** Add path sanitizing checks to bionemo.core.data.load() [BIO-409]

## Description

### Description

Make sure that tar paths from files downloaded by bionemo.core.data.load are safe and local.

### Type of changes

<!-- Mark the relevant option with an [x] -->

- [x] Bug fix (non-breaking change which fixes an issue)
- [ ] New feature (non-breaking change which adds functionality)
- [ ] Refactor
- [ ] Documentation update
- [ ] Other (please describe):

### Pre-submit Checklist

<!--- Ensure all items are completed before submitting -->

- [x] I have tested these changes locally
- [x] I have updated the documentation accordingly
- [x] I have added/updated tests as needed
- [x] All existing tests pass successfully

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->

## Summary by CodeRabbit

* **Bug Fixes**
  * Implemented path-traversal protection for ZIP and TAR archive extraction, preventing malicious archives from writing files outside their designated extraction directory during loading.

* **Tests**
  * Added comprehensive test coverage for archive extraction security validations, including path traversal attack scenarios and safe extraction verification.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9d772b2a5293`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.