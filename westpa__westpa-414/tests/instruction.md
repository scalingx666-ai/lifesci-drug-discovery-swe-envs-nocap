# Issue

**Title:** Allow bins to be autodetected with negative max values.

## Description

## Issue Number
<!--- Is this pull request related to any outstanding issues? If so, list the issue number. --->


## Describe the changes made
<!--- A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it. -->
When running `w_pdist`, If your dataset has negative values, (and that happens to be your upper bound value), then you would likely get an pcoord out of bound error. This fixes it.

## Goals and Outstanding Issues
<!--- A clear and concise list of goals (to be) accomplished. --->
- [x] Allow auto detection of bin bounds

## Major files changed
<!--- Manually list files or include a diff link in the form of: https://github.com/user/westpa/compare/<initial SHA>..<final SHA> --->
- [x] src/westpa/cli/tools/w_pdist.py

## Status
<!--- Delete bullet points that are not relevant. --->
- [x] Bug fix (non-breaking change which fixes an issue)
- [x] New feature (non-breaking change which adds functionality)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [x] My change requires a change to the documentation.
- [x] All new and existing tests passed.

## Additional context
<!--- Add any other context or screenshots about the pull request here. --->
Test code:

```
from westpa.cli.tools.w_pdist import WPDist

a = WPDist()
a.ndim = 1
a.data_range = [(-21,-1)]
a._construct_bins_from_scalar(5)
print(a.binbounds)
# Output: [array([-21.        , -16.9980198 , -12.9960396 ,  -8.99405941, -4.99207921,  -0.99009901])]
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `43ed1b907ea9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.