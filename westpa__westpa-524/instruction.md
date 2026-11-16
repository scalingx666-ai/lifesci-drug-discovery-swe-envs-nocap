# Issue

**Title:** Make RecursiveBinMapper indices and labels match up.

## Description

## Issue Number

#453 

## Describe the changes made

Change the order of the bin labels to match the bin indexing convention in `start_index.setter`. This convention assigns indices `0` through `n_not_recursed - 1` to the non-recursive bins, and indices `n_not_recursed` onward to the recursive bins.

## Goals and Outstanding Issues

Should the expected bin indices in `test2dRectilinearRecursion` be updated to the following?
```
         0                            1                      2
         +----------------------------+----------------------+
         |                            |         1.5          |
         |                            | +--------+---------+ |
         |                            | |        |         | |
         |             0              | |   4    |   5     | |
         |                            | |        |         | |
         |                            | |        |         | |
         |                            | +--------+---------+ |
        1+---------------------------------------------------+
         |            0.5             |                      |
         | +-----------+------------+ |                      |
         | |           |            | |                      |
         | |    2      |     3      | |           1          |
         | |           |            | |                      |
         | |           |            | |                      |
         | +-----------+------------+ |                      |
        2+---------------------------------------------------+

```

## Major files changed
<!--- Manually list files or include a diff link in the form of: https://github.com/user/westpa/compare/<initial SHA>..<final SHA> --->
- `src/westpa/core/binning/assign.py`

## Status
<!--- Delete bullet points that are not relevant. --->
- [x] Bug fix (non-breaking change which fixes an issue)
- [ ] New feature (non-breaking change which adds functionality)
- [ ] Breaking change (fix or feature that would cause existing functionality to change)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [ ] My change requires a change to the documentation.
- [ ] I have updated the documentation accordingly.
- [ ] I have added tests to cover my changes.
- [ ] All new and existing tests passed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6e3bc7a8c6b0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.