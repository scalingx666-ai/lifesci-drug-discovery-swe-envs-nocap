# Issue

**Title:** generalized read and plot.xvg

## Description

Hello, I attempted to modify the treatment of the .xvg files implementing

- generalization of the read.xvg function to deal with cases where time is not the x axis 
- added a .xvg file where that is the case (radial distribution function)
- changed the structure of read.xvg by using internal functions
- changed the output of read.xvg from a matrix to a data frame (subject to discussion)
- reorganized plot.xvg to make use of read.xvg
- made plot.xvg restore the par configuration after running
- modified plot.xvg to plot maximum 4 facets per row (instead of all plots in a single row)
- removing the addition of plot.xvg as a method (since there is technically no class xvg that is being implemented)
- ~~added plyr as a dependency due to the use of ldply in plot.xvg (subject to discussion, the same result could be done by using sapply > t > as.data.frame)~~

Let me know if those are found to be useful of if any modification should be done.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8edad6e667b3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.