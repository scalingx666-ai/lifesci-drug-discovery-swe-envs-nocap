# Issue

**Title:** Extra Frames in per-iter HDF5 Files + seglog_loader Fix

## Description

## Issue Number
<!--- Is this pull request related to any outstanding issues? If so, list the issue number. --->


## Describe the changes made
<!--- A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it. -->
In specific situations (like after restarting a simulation), the per-iter HDF5 file might contain extra frames for certain segments because the segment traj data might've already been written before the restart but the segment status itself did not update. After the segment is rerun after the restart, the new coordinates are also saved/appended into the per-iter H5, leading to extra frames.

The fix itself is a little messy because pytables/hdf5 API/specs does not allow one to remove rows in an `EArray`. If the existing number of rows is less than or equal the final needed number of rows (usually pcoord_len -1), extra rows are added as needed and the data for the old frames are rewritten with the new segment info. Other wise, extra rows' pointers are replaced with [-n_iter, seg_id] to distinguish from the newer frames.

This PR also fixes the broken seglog_loader and adds much needed tests for the HDF5 Framework

## Goals and Outstanding Issues
<!--- A clear and concise list of goals (to be) accomplished. --->
- [x] Do a check before writing segments into per-iter HDF5 file
- [x] new `seglog_writer` for recovering seglogs
- [x] Tests for per-iter HDF5 File (and restart/seglog loader/writer)
- [x] Fixes `Seglog_loader`

## Major files changed
<!--- Manually list files or include a diff link in the form of: https://github.com/user/westpa/compare/<initial SHA>..<final SHA> --->
- [x] src/westpa/core/h5io.py
- [x] tests/test_h5io.py
- [x] tests/conftest.py
- [x] src/westpa/core/propagators/executable.py

## Status
<!--- Delete bullet points that are not relevant. --->
- [x] Bug fix (non-breaking change which fixes an issue)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [x] My change requires a change to the documentation.
- [x] I have updated the documentation accordingly.
- [x] I have added tests to cover my changes.
- [x] All new and existing tests passed.

## Additional context
<!--- Add any other context or screenshots about the pull request here. --->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fa7d0a676fb5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.