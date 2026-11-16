# Issue

**Title:** Remove numpy data type from MAB stats output

## Description

## Issue Number
<!--- Is this pull request related to any outstanding issues? If so, list the issue number. --->


## Describe the changes made
<!--- A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it. -->
Output for MAB stats in the `west.log` file will now be a little cleaner.

Due to changes in numpy 2 string outputs, the current "MAB stats" look like:
```
################ MAB stats ################
minima in each dimension:      [np.float32(0.16191083)]
maxima in each dimension:      [np.float32(0.20319091)]
direction in each dimension:   [1]
skip in each dimension:        [0]
###########################################
```
instead of what's in numpy 1.XX:
```
################ MAB stats ################
minima in each dimension:      [0.16191083]
maxima in each dimension:      [0.20319091]
direction in each dimension:   [1]
skip in each dimension:        [0]
###########################################
```

This PR reverts printing behavior to `numpy 1.XX` format just for these lines in the `west.log`.

## Goals and Outstanding Issues
<!--- A clear and concise list of goals (to be) accomplished. --->
- [x] Cleaner output for MAB stats

## Major files changed
<!--- Manually list files or include a diff link in the form of: https://github.com/user/westpa/compare/<initial SHA>..<final SHA> --->
- [x] src/westpa/core/binning/mab.py

## Status
<!--- Delete bullet points that are not relevant. --->
- [x] Bug fix (non-breaking change which fixes an issue)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [x] I have updated the documentation accordingly.
- [x] I have added tests to cover my changes.
- [x] All new and existing tests passed.
- [x] I have read the AI POLICY document.
- [x] This PR conforms to WESTPA's AI policy.
- [x] I have declared all usage of AI in the PR description.

## Additional context
<!--- Add any other context or screenshots about the pull request here. --->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3a213bbbdec9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.