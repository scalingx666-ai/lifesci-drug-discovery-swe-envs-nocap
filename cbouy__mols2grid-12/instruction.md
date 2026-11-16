# Issue

**Title:** Add custom transform functions. Would solve #10.

## Description

This is an example implementation of how to solve #10. The demo notebook contains code that use features in RDKit 2021.3 that I commented out since I haven't upgraded yet. Please feel free to uncomment those and rerun the notebook :-)
While implementing I realised that there is a choice to make if one should format or style first. I opted to apply the format after the styling code...

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `849cf49a105b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.