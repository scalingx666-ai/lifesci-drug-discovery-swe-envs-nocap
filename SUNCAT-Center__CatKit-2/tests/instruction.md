# Issue

**Title:** Created a very no frills setup.py

## Description

- quick and dirty version using requirements.txt
- allows installation like
  `pip install git+https://github.com/<username>/CatKit.git`
-  or in `requirements.txt` like
  `git+https://github.com/mhoffman/CatKit.git#egg=catkit`
- commented out `json` and `sqlite3` since they seem builtin (keeping breaks installation)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0dfb404b92d4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.