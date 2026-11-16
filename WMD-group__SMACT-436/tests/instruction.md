# Issue

**Title:** Adding changes from develop

## Description

## Description

Changes to the `smact.utils.oxidation` module allowing for the creation of custom oxidation states lists

## Type of change

Please delete options that are not relevant.

- [ x ] New feature (non-breaking change which adds functionality)


## How Has This Been Tested?

-pytest

**Test Configuration**:

- Python version: 3.13
- Operating System: MacOS

## Reviewers

@mention individuals who you specifically want to involve in the discussion for this pull request and mention why they are needed in the discussion/why they are needed to review the pull request.

## Checklist

- [ x] My code follows the style guidelines of this project
- [x ] I have performed a self-review of my own code
- [ x] I have commented my code, particularly in hard-to-understand areas
- [x ] I have made corresponding changes to the documentation
- [x ] My changes generate no new warnings
- [x ] I have added tests that prove my fix is effective or that my feature works
- [x ] New and existing unit tests pass locally with my changes
- [ x] Any dependent changes have been merged and published in downstream modules
- [ x] I have checked my code and corrected any misspellings


<!-- This is an auto-generated comment: release notes by coderabbit.ai -->
## Summary by CodeRabbit

## Summary by CodeRabbit

**New Features**
  * Added support for generating compositions using custom oxidation states files.
  * Extended oxidation state lookup to allow retrieval of all custom oxidation states at once.

**Improvements**
  * Enhanced oxidation state filtering options for composition validity checks, allowing finer control over which states are considered.
  * Improved documentation for several functions, clarifying usage and return formats.
  * Optimised data loading by skipping irrelevant lines and clarified warning placement.

**Dependency Updates**
  * Updated multiple Python package versions for improved compatibility and stability.

**Chores**
  * Updated GitHub Actions workflows to use the latest setup action versions.
  * Minor style and formatting clean-up in documentation.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `253d325caf63`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.