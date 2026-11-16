# Issue

**Title:** One-Sided Match Targets

## Description

Implements #632 

Normal Transformations (for reference)
<img width="610" height="461" alt="image" src="https://github.com/user-attachments/assets/5eafc7fe-8caa-47f4-a879-8a7e8f336769" />

One-Sided Match corresponding to `<=1`
<img width="609" height="454" alt="image" src="https://github.com/user-attachments/assets/45ae6677-b648-4615-88a5-673ee6101d58" />

One-Sided *Mis*Match corresponding to `<=1`
<img width="616" height="461" alt="image" src="https://github.com/user-attachments/assets/fb1e59a9-92a8-4135-b92a-c1daf6a96198" />

Amended doc on fork: https://scienfitz.github.io/baybe-dev/latest/userguide/targets.html#advanced-matching-options

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6abf49fd39a0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.