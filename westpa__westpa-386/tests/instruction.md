# Issue

**Title:** Pinning to Numpy < 2

## Description

**Issue Number.** Is this pull request related to any outstanding issues? If so, list the issue number.  
#372 #374  

**Describe the changes made.** A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it.  
Pinning to numpy < 2 for the time being until official release of numpy 2.0 (and #374). Better be safe than sorry. 

**Goals and Outstanding Issues.** A clear and concise list of goals (to be) accomplished.  
- [x] Pin to numpy<2 until #374 is merged

**Major files changed.**  
- [x] pyproject.toml
- [x] setup.py

**Status.**
- [x] Bug fix (non-breaking change which fixes an issue)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [x] I have updated the documentation accordingly.
- [x] All new and existing tests passed.

**Additional context.** Add any other context or screenshots about the pull request here.  


Played around with the numpy `2.0b1` release and it wasn't working due to the multitude of other WESTPA dependencies that requires `numpy < 2`. I'm getting a lot of import errors, especially in the Cython sections (which may or may not be due to a broken install due to dependencies). 

```
E   ImportError: numpy.core.multiarray failed to import (auto-generated because you didn't call 'numpy.import_array()' after cimporting numpy; use '<void>numpy._import_array' to disable if you are certain you don't need it).      
```

While #374 ruff linting currently says it's fine, I'm not 100% sure our CPython numpy code are well covered and it's very difficult to check until everything else upstream supports `numpy>=2`.


List of dependencies that don't work with numpy 2.0 just yet
```
ERROR: pip's dependency resolver does not currently take into account all the packages that are installed. This behaviour is the source of the following dependency conflicts. 
ndfes 1.8 requires joblib, which is not installed. 
scipy 1.12.0 requires numpy<1.29.0,>=1.22.4, but you have numpy 2.0.0b1 which is incompatible.
pandas 2.2.1 requires numpy<2,>=1.23.2; python_version == "3.11", but you have numpy 2.0.0b1 which is incompatible.   
contourpy 1.2.0 requires numpy<2.0,>=1.20, but you have numpy 2.0.0b1 which is incompatible. 
matplotlib 3.8.3 requires numpy<2,>=1.21, but you have numpy 2.0.0b1 which is incompatible. 
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `24d45db54ba2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.