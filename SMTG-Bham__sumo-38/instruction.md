# Issue

**Title:** Fix missing floating point on y-axis of optplots.

## Description

In sumo-optplot default behavior rounded y-axis to an apparent float value. 
![image](https://user-images.githubusercontent.com/27951554/48714298-584bf080-ec0a-11e8-92dd-871cd6984028.png).

Format string changed from 'g' to 'f' to allow floating point.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f93350796c5c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.