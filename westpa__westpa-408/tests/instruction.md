# Issue

**Title:** allow users to specify executable config in west.data.datasets

## Description

## Issue Number
<!--- Is this pull request related to any outstanding issues? If so, list the issue number. --->


## Describe the changes made
<!--- A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it. -->
A somewhat popular wishlist item, in your `west.cfg`, you can now specify relevant dataset keywords for the propagator executable within the same section as that for the data manager.

All the options documented [here](https://github.com/westpa/westpa/wiki/Configuration-File#propagator-executable) should work, since there are no overlap in keywords with [that](https://github.com/westpa/westpa/wiki/Configuration-File#data-manager) for the data manager.

Older behavior is preserved and will have precedence.  This "new" behavior will only occur when `west.executable.datasets` is None (i.e., not declared/keyword doesn't exist/explicitly set as None).

Example:
```
# Previously:
west:
    data:
        datasets:  # Section for data manager
            - name:         coord
              scaleoffset:  3
              dtype:        float32
    executable:  # Separate section for propagator, 'coord' needed to be listed twice to work properly
        datasets:
            - name:         coord
              loader:       npy_loader
              enabled:      true
```

```
# Also possible now
west:
    data:
        datasets:  # All keywords for 'coord' are combined in one section
            - name:         coord
              scaleoffset:  3
              dtype:        float32
              loader:       npy_loader  # These two are for the propagator executable
              enabled:      true
```


## Goals and Outstanding Issues
<!--- A clear and concise list of goals (to be) accomplished. --->
- [x] Easier west.cfg dataset specification
- [x] Test for executable

## Major files changed
<!--- Manually list files or include a diff link in the form of: https://github.com/user/westpa/compare/<initial SHA>..<final SHA> --->
- [x] src/westpa/core/propagators/executable.py
- [x] tests

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ee87379ec391`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.