# Issue

**Title:** reinitialize trainer after fitting

## Description

**Problem:**
The lightning trainer retains all training data, making the joblib dump unnecessary large.

**Solution:**
Reinitialize the trainer after model fitting to clear history.

**ToDos**
 - [x] Fix Problem

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2f9baee03f82`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.