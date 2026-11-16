# Issue

**Title:** Add links to RTD

## Description

So as discussed I added link to all estimators, now they temporally point to `latest` version of the docs. 

I assume, that as soon as we will have first tagged version (v0.4.7) RTD will start generating versioned docs and we will be able for each estimator to point to the version of the `scikit-mol` used by user

Also changed `use_directory_urls` to `true` so how pages will have no `.html` extension

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7290b0323bcd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.