# Issue

**Title:** Oxidation states filters added to the smact_validity function

## Description

## Description

Added the ability to create a customized oxidation states list within the smact_validity function. It is expected to significantly simplify the usage of smact_validity with more realistic oxidation states filters.

## Type of change


- New feature (non-breaking change which adds functionality)


## How Has This Been Tested?

-pytest

**Test Configuration**:

- Python version: 3.13.
- Operating System: MacOs

## Reviewers

@AntObi @hspark1212 

## Checklist

- [ x] My code follows the style guidelines of this project
- [ x] I have performed a self-review of my own code
- [ x] I have commented my code, particularly in hard-to-understand areas
- [ x] I have made corresponding changes to the documentation
- [ x] My changes generate no new warnings
- [ x] I have added tests that prove my fix is effective or that my feature works
- [ x] New and existing unit tests pass locally with my changes
- [ x] Any dependent changes have been merged and published in downstream modules
- [ x] I have checked my code and corrected any misspellings

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->

## Summary by CodeRabbit

* **New Features**
  * Added new options for filtering oxidation states in composition validity checks, including consensus levels, zero-inclusion, and commonality thresholds.

* **Bug Fixes**
  * Improved logic in screening filters for more accurate composition validation.

* **Documentation**
  * Enhanced runtime output with additional print statements to provide better visibility into data processing steps.

* **Style**
  * Improved code readability with minor formatting adjustments.

* **Refactor**
  * Updated function signatures to support more flexible parameter types and options.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7969ba69c803`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.