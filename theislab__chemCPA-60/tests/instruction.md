# Issue

**Title:** Adjust sweeps for better adv loss

## Description

I looked at the main adversary parameter differences between the models with the best (=lowest) perturbation disentanglement score and those with the worst (=highest) score and adjusted them.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `35ec12ab4db6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.