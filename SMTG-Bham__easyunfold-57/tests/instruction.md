# Issue

**Title:** Multiple `PROCAR` parsing fix

## Description

This fixes an issue reported by @Iamkeli when parsing multiple (`LORBIT = 14`) `PROCAR`s at once, for doing `easyunfold unfold plot-projections`.

Basically, the issue was the previous code relied on finding the next double-blank-line in the `PROCAR` as the marker between k-points (when skipping a previously-parsed kpoint for efficiency), but this is not the case for `LORBIT = 14` which has 2 blank lines between each band and 3 blank lines between k-points. The updated implementation is more robust, directly matching the `"k-point"` string.

Working as expected with updated implementation (here showing the contributions of a resonant donor to the CB):
![image](https://github.com/user-attachments/assets/350211b3-d07f-4e4a-a812-c672aefc820d)

- I also added a small update to avoid a `DeprecationWarning` with the latest version of `monty`

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->

## Summary by CodeRabbit

- **Bug Fixes**
	- Updated file handling to use a consistent text encoding, reducing issues with special characters.
- **Refactor**
	- Streamlined internal processing of grid-based numerical data for enhanced clarity and performance.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7f772bf91576`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.