# Issue

**Title:** allow tstate files to contain empty line(s) and comments

## Description

**Issue Number.** Is this pull request related to any outstanding issues? If so, list the issue number.  


**Describe the changes made.** A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it.  
Line parsing of the target state file is written differently from the code for basis state, such that you can't have comments or empty lines at the bottom of the file. This PR will allow empty lines, trailing spaces and comments to be added into the target state file.

**Goals and Outstanding Issues.** A clear and concise list of goals (to be) accomplished.  
- [x] Better user experience when specifying target states 

**Major files changed.**  
- [x] src/westpa/core/states.py

**Status.**
- [x] Bug fix (non-breaking change which fixes an issue)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [x] All new and existing tests passed.

**Additional context.** Add any other context or screenshots about the pull request here.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `60539e6235eb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.