# Issue

**Title:** preliminary handling of Gaussian labeling error; bug fix for neg freq exceptions

## Description

Hey Jason, I include here a temporary approach to handle any problems with the Gaussian labels not matching by giving them a different status called "inspect" in the job manager. This approach lets the files still be accessible if needed later but the other jobs can be properly uploaded to the db. Also there was a bug with not detecting negative frequencies if the jobs all terminated normally so I switched the order of checking for exceptions which should catch this. Thanks!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `168acb92812d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.