# Issue

**Title:** Generating compositions using custom oxidation states lists / Memory optimization

## Description

# Pull Request Template

## Description
The pull request contains memory-optimized generate_composition_with_smact function and its dependencies to make it suitable for mapping the full quaternary space. Errors while using custom oxidation states lists were resolved by using pre-filtering.

Created a second generate_composition_with_smact function (generate_composition_with_smact_custom) particularly suited for custom oxidation states lists. The decision to a create separate function was taken to optimize the memory usage.

Fixes # (issue)

## Type of change

Please delete options that are not relevant.


- [  x ] New feature (non-breaking change which adds functionality)

## How Has This Been Tested?

Please describe the tests that you ran to verify your changes. Provide instructions so we can reproduce. Please also list any relevant details for your test configuration

- pytest

**Test Configuration**:

- Python version: 3.13
- Operating System: MacOS

## Reviewers

@mention individuals who you specifically want to involve in the discussion for this pull request and mention why they are needed in the discussion/why they are needed to review the pull request.

## Checklist

- [ x ] My code follows the style guidelines of this project
- [x ] I have performed a self-review of my own code
- [ x] I have commented my code, particularly in hard-to-understand areas
- [x ] I have made corresponding changes to the documentation
- [ x] My changes generate no new warnings
- [ x] I have added tests that prove my fix is effective or that my feature works
- [ x] New and existing unit tests pass locally with my changes
- [ x] Any dependent changes have been merged and published in downstream modules
- [x ] I have checked my code and corrected any misspellings

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->

## Summary by CodeRabbit

* **New Features**
  * Added a new function to generate compositions using custom oxidation states files.
* **Improvements**
  * Enhanced data loading to skip non-relevant lines for improved performance.
  * Extended oxidation state lookup to support returning all available oxidation states.
  * Clarified and updated documentation for several functions, including guidance on custom oxidation state usage.
* **Chores**
  * Updated pre-commit configuration to use a newer version of a code quality tool.
  * Minor formatting adjustments in documentation.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0442b5969760`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.