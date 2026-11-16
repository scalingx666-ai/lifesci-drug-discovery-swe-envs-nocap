# Issue

**Title:** Simple pip reqs

## Description

I updated the pip requirements file (in pip/simple_requirements.txt) to ignore all dependencies that are installed by the main programs we require. I haven't verified that it works on LC or with maestro, GMD or atomsci.clients so it's not ready to actually merge yet, but I wanted to ask for help in testing it out. It passed all the unit and integrative tests on my system. 
- Less packages to keep track of.
- More up-to-date packages managed as others' dependencies instead of explicit requirements on our end.
- This includes updated packages such as pandas and numpy that had a few small breaking changes. I fixed these.
- PyYAML 6.0.1 is still unusable because it's referenced in several json readers; this requirement is frozen at 5.4.1

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6526787f53c0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.