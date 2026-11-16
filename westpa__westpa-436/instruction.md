# Issue

**Title:** Fixing the MAB skip function in 2+ dimensions.

## Description

## Issue Number
Not related to an open issue, but I have reported this in the [westpa-users mailing list](https://groups.google.com/g/westpa-users/c/qBRihv_6stA/m/HKptPU5wCAAJ).

Currently MAB skipping is broken when using 2D pcoords. Presumably it works with a 1D pcoord, but when I attempted to use it with a 2-dimensional progress coordinate and MAB skipping along particular dimensions, it failed to populate the bins properly. I believe this is due to some erroneous break statements in the loop over dimensions when skip is enabled.

## Describe the changes made

- Parsing the mab.py code was quite difficult, and it seems overly complex with extra for loops. I refactored a lot of it by renaming variables for clarity, removing duplicated code, adding comments, and converting for loops to vectorized commands where possible. I believe the code now runs significantly faster for large sets of input coords.
- I fixed the bug in skipping by refactoring the calculation of MAB bins, carefully dissecting out the erroneous break statements to work in 2D+. All code changes are contained within mab.py.
- I abstracted parts of the code into sub-functions to help with readability and maintainability.
- When `skip` is active, the code now re-assigns the number of linear bins along the skipped dimension to be `1`, irrespective of the input number of bins along that dimension. It now also properly prevents assignment of any walker to special bins along that dimension.
- `direction=86` correctly ignores leading/lagging bins and only assigns bottleneck bins (in both directions) if `bottleneck=True`. Therefore, `direction=86` with `bottleneck=False` now disables all special MAB bins along that dimension. **This is changed behavior in reporting**, as previously `bottleneck=False` reported a single bottleneck bin per dimension with `direction=86`. The behavior and bin reporting now match, ensuring this parameter works as expected.
- Notably, `maxdiff` and its flipped version are now initialized to `-np.inf` rather than 0. This way, a bottleneck bin will be found even if the largest Z is negative (notation from the MAB paper). Now, if no walker has a positive Z, a non-boundary walker with the smallest negative Z will be assigned to a bottleneck bin instead (this will typically be a near-boundary walker). **This is changed behavior**, and it makes all bottleneck bins more likely to be populated, particularly when there are few walkers within a MAB zone.

MAB now creates the expected number of bins with `direction`, `skip`, `bottleneck`, and `nbins` all playing nicely together. Here are some example configurations tested with a 2D pcoord.
**Example 1**
> direction: [0, 0]
> skip: [0, 0]
> bottleneck: true 
> nbins: [5, 1]

Produces 5x1 linear + 2x2 boundary + 2x2 bottleneck = 13 total MAB bins

**Example 2**
> direction: [1, 0]
> skip: [0, 1]
> bottleneck: true 
> nbins: [5, 1]

Produces 5 linear + 1 boundary + 1 bottleneck = 7 total MAB bins

**Example 3**
> direction: [-1, 86]
> skip: [0, 0]
> bottleneck: false
> nbins: [5, 5]

Produces 5x5 linear + 1 boundary + 0 bottleneck = 26 total MAB bins

**Example 4**
> direction: [-1, 86]
> skip: [0, 1]
> bottleneck: true
> nbins: [5, 5]

Produces 5 linear + 1 boundary + 1 bottleneck = 7 total MAB bins

## Goals and Outstanding Issues
- The tests should be refactored.
- MAB bin occupancy reporting may not always be accurate for bottleneck bins. This is an ongoing bug which is not addressed by these changes.

## Major files changed
- [mab.py](https://github.com/HScheiber/westpa/compare/579af04a62ab9883bfaf9468932a324acb0fbdae...d75ab2f6e66ade502a8920d76c4da117aea3b748)
-  (new tests added for MAB code)
- tests/ref/mab_assignments_ref.h5, which contains 2D and 3D MAB binning test expectation results.

## Status
- [X] Bug fix (non-breaking change which fixes an issue)
- [ ] New feature (non-breaking change which adds functionality)
- [X] Breaking change (fix or feature that would cause existing functionality to change)
- [X] I have read the CONTRIBUTING document.
- [X] My code follows the code style of this project.
- [X] My change requires a change to the documentation.
- [X] I have updated the documentation accordingly.
- [X] I have added tests to cover my changes.
- [x] All new and existing tests passed.

## Additional context
- [Related westpa-users discussion post 1](https://groups.google.com/g/westpa-users/c/qBRihv_6stA/m/HKptPU5wCAAJ)
- [Related westpa-users discussion post 2](https://groups.google.com/g/westpa-users/c/NFFCwBBL5Uw)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `579af04a62ab`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.