# Issue

**Title:** Remove pickle use from SCDL [BIO-408]

## Description

### Description

Remove the allow_pickle=True option when loading feature name paths in scdl.

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
- [ ] I have updated the documentation accordingly
- [x] I have added/updated tests as needed
- [x] All existing tests pass successfully

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->

## Summary by CodeRabbit

* **New Features**
  * Dataset labels now stored in JSON format for improved portability and safety.

* **Bug Fixes**
  * Enhanced error handling with clearer messages for missing or corrupted label files.
  * Added backward compatibility with deprecation warnings for legacy label formats.

* **Tests**
  * Added tests for label format migration and error scenarios.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9d772b2a5293`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.