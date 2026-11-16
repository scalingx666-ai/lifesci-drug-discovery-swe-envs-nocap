# Issue

**Title:** Add pytest CI (Github Actions)

## Description

## Background

This adds 2 pytest actions:
1. unit
2. integrative
The integrative tests are naively chunked at the moment between `integrative-1` and integrative-2`

I think there should be an issue ticket created to rewrite some tests to be folderpath agnostic. If you have filename collision issues, they can be solved by other means. The benefit can be gained when you run parallel test workers. See how the unit test differs, whereas the integrative tests will be run sequentially if we use `integrative_batch_tests.sh`. I think this will make a difference since the integration tests take about 29m  :grimacing: 
![image](https://github.com/user-attachments/assets/30f7fe90-6df7-4180-a6a1-c471da245724)

Once you merge this, you should get builds for every commit. I think it might make sense to at least have unit tests be a required step before merging. 

I am happy to guide you through those GitHub settings changes

## References
- [example pytest-unit](https://github.com/mass-matrix/AMPL/actions/runs/10274394350/job/28431011780) From https://github.com/mass-matrix/AMPL

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d968f51f6c75`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.