# Issue

**Title:** Plot roundtrip validations

## Description

After a few discussions, we decided to plot the validation "roundtripping" results for the manuscript using a nested bar chart instead of a Sankey diagram or more complicated figure.  The main purpose of this PR is to update the R code for the paper.

The sbu.cpp code now reports detailed linker statistics, too, like the coordination number, which could be useful for a new figure in the paper (and more directly provides the linker SMILES than parsing the MOFid).  The MOFkey has also been truncated to only include the first layer of the InChIKey to remove the redundant characters "-UHFFFAOYSA-N".

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6452d984fbaf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.