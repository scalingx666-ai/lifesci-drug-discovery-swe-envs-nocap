# Issue

**Title:** [WIP] ElementEmbeddings integration

## Description

# ElementEmbeddings Integration

## Description

* Wrappers to ElementEmbeddings


## Type of change

- [x] New feature (non-breaking change which adds functionality)

- [x] This change requires a documentation update

## How Has This Been Tested?

(TODO)
- [ ] Test A
- [ ] Test B

**Test Configuration**:

- Python version: 3.11
- Operating System: macOS

## Reviewers



## Checklist

- [x] My code follows the style guidelines of this project
- [x] I have performed a self-review of my own code
- [x] I have commented my code, particularly in hard-to-understand areas
- [x] I have made corresponding changes to the documentation
- [x] My changes generate no new warnings
- [x] I have added tests that prove my fix is effective or that my feature works
- [x] New and existing unit tests pass locally with my changes
- [x] Any dependent changes have been merged and published in downstream modules
- [x] I have checked my code and corrected any misspellings

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->
## Summary by CodeRabbit

## Release Notes

* **New Features**
  * Added element embeddings integration tutorial demonstrating feature vector generation for chemical compositions.
  * Introduced composition featuriser functionality for converting chemical formulas to numerical feature vectors.
  * Added SmactFilterOutputs enum enabling flexible formatting of chemical formula screening results.
  * Enabled SmactStructure instances to be used in sets and as dictionary keys via hashing.

* **Documentation**
  * Updated README with additional resource badge.

* **Chores**
  * Updated build tool and linting dependencies to latest versions.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `672381ed3153`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.