# Issue

**Title:** Fixed the labelling when printing the symmetry information

## Description

Just a super simple fix. Originally, when you run `easyunfold generate` it prints the primitive cell information under the heading supercell cell information and vice versa.

<img width="695" alt="unfold_orig" src="https://user-images.githubusercontent.com/56972784/194023961-d94b1b00-80cf-44d1-b460-283325691c50.png">

Now with the fix:

<img width="694" alt="unfold_fix" src="https://user-images.githubusercontent.com/56972784/194023996-7011807e-4fe2-4081-b564-9c380509b6e3.png">

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f64198fdc15b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.