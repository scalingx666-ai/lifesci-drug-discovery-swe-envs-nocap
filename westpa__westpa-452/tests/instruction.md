# Issue

**Title:** Allow WESS and WEED to detect when a simulation has been truncated

## Description

## Issue Number

## Describe the changes made
Previously, when w_truncate was used to truncate a simulation, WESS and WEED would not execute reweighting until the simulation progressed beyond the original last reweighting iteration. This is because they used an attribute field in the west.h5 to store the last reweighting iteration, which would overwrite each time reweighting occurs. This value would stay static after truncating the simulation, leading to undesired behavior of WESS and WEED not reweighting at all after truncating, since the last reweighting occurred in a future iteration.

To fix this, I instead stored the reweighting history data in a dataset. This is more appropriate since attributes should be used for metadata, and it allows a running history of reweighting events to be recorded. I also added a check to evaluate if the last reweighting event is in a future iteration. If this is the case, the reweighting history dataset will be truncated to only include values less than n_iter.

## Goals and Outstanding Issues
- [x] Made WESS and WEED compatible with w_truncate

## Major files changed
- [x] src/westpa/westext/weed/weed_driver.py
- [x] src/westpa/westext/wess/wess_driver.py

## Status
- [x] Bug fix (non-breaking change which fixes an issue)
- [ ] New feature (non-breaking change which adds functionality)
- [ ] Breaking change (fix or feature that would cause existing functionality to change)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [ ] My change requires a change to the documentation.
- [ ] I have updated the documentation accordingly.
- [ ] I have added tests to cover my changes.
- [ ] All new and existing tests passed.

## Additional context

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1af3dcf7c616`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.