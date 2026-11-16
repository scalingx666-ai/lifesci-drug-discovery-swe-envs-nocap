# Issue

**Title:** Fix to make sure recursive bin labels match up with bins index

## Description

**Issue Number.** Is this pull request related to any outstanding issues? If so, list the issue number.  
https://groups.google.com/g/westpa-users/c/zBmbMlsXxPY

**Describe the changes made.** A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it.  
Depending on the order the recursive binning is made, `RecursiveBinMapper._recursion_target` (a dictionary of constituent bin mappers) maybe in different orders. This causes a mismatch of how [bin indices are labeled](https://github.com/westpa/westpa/blob/westpa2/src/westpa/core/binning/assign.py#L363-L382) and [how bin labels are generated](https://github.com/westpa/westpa/blob/westpa2/src/westpa/core/binning/assign.py#L352-L354). This might be a vestige of when dictionaries aren't ordered based on insertion (before py3.6).

Guarantee that the order of `RecursiveBinMapper._recursion_target` is sorted by key, which is necessary for the labels to match up.  This fix is coded this way to make sure bins are labeled in monotonically increasing order (by each dimension).

`RecursiveBinMapper._recursion_map`, which indicates if the bin is recursive, is already indexed based on position (via the key in `_recursion_target`), so should not be affected. `RecursiveBinMapper._recursion_target` is also indexed via key, so should work as expected except when it's called via `RecursiveBinMapper._recursion_target.values()` (i.e. in `RecursiveBinMapper.labels`).

Haven't tested on restarting older simulations so might be worth double checking that before merging.

**Goals and Outstanding Issues.** A clear and concise list of goals (to be) accomplished.  
- [x] Make sure bin indices line up with bin labels

**Major files changed.**  
- [x] src/westpa/core/binning/assign.py

**Status.**
- [x] Bug fix (non-breaking change which fixes an issue)
- [x] Breaking change (fix or feature that would cause existing functionality to change)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [x] My change requires a change to the documentation.
- [x] I have updated the documentation accordingly.
- [x] I have added tests to cover my changes.
- [x] All new and existing tests passed.

**Additional context.** Add any other context or screenshots about the pull request here.  

Short code snippet to test. Calling `list(bin_mapper.labels)` is also useful to make sure they are in the right order.
```
from westpa.core.binning import RecursiveBinMapper, RectilinearBinMapper

def make_mapper():
    mapper_outer=RectilinearBinMapper([[0,5,float('inf')],[0, float('inf')], [0, float('inf')]])
    second_bin=RectilinearBinMapper([[5,float('inf')], [0, 1, 2, 3, float('inf')], [0, float('inf')]])
    first_bin=RectilinearBinMapper([[0,5], [0,15.0, float('inf')], [0, float('inf')]])
    
    bin_mapper = RecursiveBinMapper(mapper_outer)
    bin_mapper.add_mapper(second_bin, [10,2,5])
    bin_mapper.add_mapper(first_bin, [1, 2, 5])

    print(bin_mapper._recursion_targets)
    # should print before fix:
    # {1: <RecursiveBinMapper at 0x12061f750 with 4 bins>, 0: <RecursiveBinMapper at 0x121d122d0 with 2 bins>}
    # should print after fix:
    # {0: <RecursiveBinMapper at 0x106fc4e90 with 2 bins>, 1: <RecursiveBinMapper at 0x106f9ead0 with 4 bins>}

    return bin_mapper

def make_mapper2():
    mapper_outer=RectilinearBinMapper([[0,5,float('inf')],[0, float('inf')], [0, float('inf')]])
    second_bin=RectilinearBinMapper([[5,float('inf')], [0, 1, 2, 3, float('inf')], [0, float('inf')]])
    first_bin=RectilinearBinMapper([[0,5], [0,15.0, float('inf')], [0, float('inf')]])
    
    bin_mapper = RecursiveBinMapper(mapper_outer)
    bin_mapper.add_mapper(first_bin, [1, 2, 5])
    bin_mapper.add_mapper(second_bin, [10,2,5])

    print(bin_mapper._recursion_targets)
    # should print {0: <RecursiveBinMapper at 0x106fc4e90 with 2 bins>, 1: <RecursiveBinMapper at 0x106f9ead0 with 4 bins>}

    return bin_mapper

bm = make_mapper()
bm = make_mapper2()

```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bbd027f8eae2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.