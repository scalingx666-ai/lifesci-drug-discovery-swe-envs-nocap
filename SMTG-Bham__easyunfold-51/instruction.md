# Issue

**Title:** Improve k point labelling when there are discontinuities in the path

## Description

Combine the labels of points when there is a discontinuity. Such points are labelled by the `A|B` sytax. 

Example: 

![figure](https://github.com/user-attachments/assets/eae950bf-a54e-4b79-97e9-ca47a6091fbf)

This fixes issue #49 where the flat bands are caused using the apparent distance between two k-point where the path was discontinuous.

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->
## Summary by CodeRabbit

- **New Features**
	- Updated version to 0.3.7, indicating minor improvements and bug fixes.
	- Introduced a new parameter in the k-point distance calculations to control the visibility of discontinuities.
	- Added a new method for generating combined k-point labels, enhancing k-point representation.

- **Bug Fixes**
	- Improved robustness in retrieving k-point labels.

- **Documentation**
	- Added citation for L. Zhang et al.'s study to the README and documentation, enhancing user resources.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `016d0afe2c7a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.