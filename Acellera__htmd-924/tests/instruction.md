# Issue

**Title:** Set default ncpus to 1. Rename ncpus to njobs to follow nomenclature

## Description

We have had a multitude of issues both personally and our users with parallelism. On some machines it works on others it doesn't. Usually it needs huge amounts of RAM for many trajectories which most users don't have. Adria had issues with relative paths in adaptive. I have had issues with filtering on a 32GB RAM machine, etc. Changes in the default backend of joblib also caused issues.

Instead of doing support and losing users we will make the default 1 thread and the users can find the options for parallelism in the docs.

Also since we might start issuing more HTMD version warnings, I made a way to permanently disable specific version warnings.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4b89ac4a866b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.