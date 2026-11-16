# Issue

**Title:** Dropping `oldest-supported-numpy` for python>=3.9

## Description

**Issue Number.** Is this pull request related to any outstanding issues? If so, list the issue number.  
#372 

**Describe the changes made.** A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it.  

As I mentioned in  `oldest-supported-numpy` has been [deprecated](https://github.com/scipy/oldest-supported-numpy) in favor of the built-in C API exporting feature of numpy>=1.25.0.

This drops `oldest-support-numpy` for python >=3.9 in light of `numpy2`'s eventual release.

**Goals and Outstanding Issues.** A clear and concise list of goals (to be) accomplished.  
- [x] drop `oldest-support-numpy` for python >=3.9

**Major files changed.**  
- [x] pyproject.toml

**Status.**
- [x] Bug fix (non-breaking change which fixes an issue)
- [x] Breaking change (fix or feature that would cause existing functionality to change)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [x] All new and existing tests passed.

**Additional context.** Add any other context or screenshots about the pull request here.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `080367e9ed7b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.