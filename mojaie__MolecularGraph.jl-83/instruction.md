# Issue

**Title:** Commented checks for atom visibility (issues/82)

## Description

I did it!


`isatomvisible_[i] || continue` turned out not to be necessary as graphs plotted by it either don't show up due to indices not being there in the first place, or need to be shown (and currently dont). 

![image](https://user-images.githubusercontent.com/11844340/215942445-4574c10e-5293-4914-8b2c-f755170a5bcd.png)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e92782732502`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.