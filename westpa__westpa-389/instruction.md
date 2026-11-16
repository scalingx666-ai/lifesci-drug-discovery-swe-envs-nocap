# Issue

**Title:** specify errors to be HDF5 Framework related

## Description

**Issue Number.** Is this pull request related to any outstanding issues? If so, list the issue number.  
 #373 

**Describe the changes made.** A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it.  
Aims to address #373's concerns for cases where trajectories are not saved correctly in the HDF5 Framework.

**Goals and Outstanding Issues.** A clear and concise list of goals (to be) accomplished.  
- [x] Better indicate that the HDF5 Framework is not working as intended

**Major files changed.**  
- [x] src/westpa/core/propagators/executable.py

**Status.**
- [x] Bug fix (non-breaking change which fixes an issue)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [x] All new and existing tests passed.

**Additional context.** Add any other context or screenshots about the pull request here.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `601316440f35`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.