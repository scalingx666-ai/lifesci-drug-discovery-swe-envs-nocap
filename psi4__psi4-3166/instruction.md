# Issue

**Title:** Make aliases for MGGA_ DFTs and PW91 consistent

## Description

## Description
The `MGGA_MVSh` functional [is aliased to `MVSh`](https://github.com/psi4/psi4/blob/bf9d20fc579995b0bc2c38b749a31c0d6f85c82e/psi4/driver/procrouting/dft/hyb_functionals.py#L326). This is inconsistent with `MGGA_MS0`, `MGGA_MS1`, `MGGA_MS2`, and `MGGA_MVS`. This change adds an alias for `MS0`, `MS1`, `MS2`, and `MVS`, respectively.

**EDIT:** Similarly, there are two more functionals with inconsistent naming: PW91 and mPWPW. LibXC refers to these as PW91 and mPW91, respectively, while the mPWPW paper refers to them as PWPW and mPWPW, respectively. Hence, I added an alias of `PWPW` for `PW91`; and an alias of `mPW91` for `mPWPW`.


## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] Alias `MGGA_MS0`, `MGGA_MS1`, `MGGA_MS2`, and `MGGA_MVS` to `MS0`, `MS1`, `MS2`, and `MVS`, respectively.
- [x] Alias `PW91` to `PWPW`; and `mPWPW` to `mPW91`.

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] Alias `MGGA_MS0`, `MGGA_MS1`, `MGGA_MS2`, and `MGGA_MVS` to `MS0`, `MS1`, `MS2`, and `MVS`, respectively.
- [x] Alias `PW91` to `PWPW`; and `mPWPW` to `mPW91`.

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bf9d20fc5799`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.