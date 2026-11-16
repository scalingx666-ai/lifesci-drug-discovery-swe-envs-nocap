# Issue

**Title:** Add support for testing and wheel-building on macos-arm64 (Apple Silicon)

## Description

## Issue Number
<!--- Is this pull request related to any outstanding issues? If so, list the issue number. --->


## Describe the changes made
<!--- A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it. -->
Adds ability to build macos-arm64 wheels for WESTPA. Users will still have to have their own HDF5 install to install our upstream dependency `PyTables` on Apple Silicon Macs.  See notes [here](https://github.com/westpa/westpa/wiki/Alternate-Installation-Instructions#macos-aarch64-apple-silicon).

Here's a link of the CI (build workflow) showing it works.
https://github.com/jeremyleung521/westpa/actions/runs/8853098441

## Goals and Outstanding Issues
<!--- A clear and concise list of goals (to be) accomplished. --->
- [x] build macos-arm64 wheels for WESTPA
- [x] test on both macos-arm64 and macos-x86-64

## Major files changed
<!--- Manually list files or include a diff link in the form of: https://github.com/user/westpa/compare/<initial SHA>..<final SHA> --->
- [x] .github folder

## Status
<!--- Delete bullet points that are not relevant. --->
- [x] New feature (non-breaking change which adds functionality)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [x] My change requires a change to the documentation.
- [x] I have updated the documentation accordingly.
- [x] I have added tests to cover my changes.
- [x] All new and existing tests passed.

## Additional context
<!--- Add any other context or screenshots about the pull request here. --->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f6a01ecdd687`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.