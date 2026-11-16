# Issue

**Title:** Add `--extremum-eigenvalue` option and fixes for effective mass code

## Description

@Iamkeli flagged that in her system where she wanted to fit the effective mass of a degenerately-doped supercell, the VBM/CBM detection failed due to high occupancy of the CBM.

This adds the option to specify `--extremum-eigenvalue`, to help in band edge determination/fitting when auto-detection fails. This is a part of the code I haven't worked on so much.

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->

## Summary by CodeRabbit

- **New Features**
  - Added a command option for manually specifying the band-edge eigenvalue, giving users more control over effective mass calculations when automatic detection is not sufficient.

- **Documentation**
  - Updated the description for the band filter option to enhance clarity and improve user experience.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7f772bf91576`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.