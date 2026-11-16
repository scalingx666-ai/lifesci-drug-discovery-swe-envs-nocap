# Issue

**Title:** Minor improvements for generation of dataset of reaction profiles.

## Description

- Reading the `output.csv` as a data frame (with pandas) can be problematic because of the first line, removing the line you will have a proper data frame with well-structured columns. Also, that information is printed in the `methods.txt` file. 
- For specific purposes, it is not necessary a final single point, add it as a boolean (set to True by default). Sort of related to pull request  #330.
- The convergence criterion for the optimization with Gaussian should be set to `Tight`. 
- Implemented bug #358.

## Checklist

* [ ] The changes include an associated explanation of how/why
* [ ] Test pass
* [ ] Documentation has been updated
* [ ] Changelog has been updated

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8284a7c26b7b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.