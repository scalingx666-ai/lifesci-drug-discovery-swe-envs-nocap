# Issue

**Title:** Feature request: Allow custom criteria for exclude_nca function

## Description

Relates to feature request in #436 


### Implementation:

Introduction of `exclude_nca_by_param`: A generic function to centralize logic for excluding results based on parameter thresholds. I have two proposals on how to use this function, however please feel free to just choose one (or none) of them if they don't seem useful. I can reset my commits. I would suggest using this function for:

- `User use`. The function will allow users to customize their exclusion criteria  for their results as well as the affected parameters. This can be helpful for users with special needs or interests.

- `Code refactoring`. I recommend using it to build the other `exclude_nca` specific functions. This in my opinion will simplify: 1) Simplify code maintenance and future developments, 2) Reduce redundancy in the testing files, 3) Homogenize the functions behavior, which currently was for example using different strategies in the parameter names for the exclusion messages. 

### Other changes relevant to mention and/or discuss:
- `Names to use for the parameters`. In the exclusion messages at first I was thinking in using something as the `pretty names`. However, they won't seem great for certain parameters (i.e, `adj.r.squared`)

* **Special case for `exclude_nca_tmax`:** This function will work as the others and its message will be `tmax < X` instead of `tmax <= X`. However, if it is mandatory there are easy solutions to solve this like the one in `exclude_nca_tmax_0`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1021712ab9b0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.