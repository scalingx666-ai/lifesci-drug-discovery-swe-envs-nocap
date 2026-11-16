# Issue

**Title:** Update band interpolation

## Description

Just a small PR which switches from using `pcolormesh` to `imshow` in plotting, which then makes use of built-in interpolation and reduces some of the graininess of plotted grids mentioned in

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->
## Summary by CodeRabbit

- **Documentation**
  - Fixed a minor grammatical error in documentation for crystalline silicon unfolding process
  - Updated comment clarity in spectral function plotting method

- **Improvements**
  - Modified spectral function visualization technique using `imshow` for better rendering
  - Enhanced parameter handling in plotting methods for clarity and consistency
  - Updated exception handling configuration for stricter checks on caught exceptions
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7f772bf91576`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.