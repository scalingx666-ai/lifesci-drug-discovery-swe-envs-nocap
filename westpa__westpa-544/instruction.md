# Issue

**Title:** Fix Hang in Python 3.14 GH Actions

## Description

## Issue Number
<!--- Is this pull request related to any outstanding issues? If so, list the issue number. --->


## Describe the changes made
<!--- A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it. -->
https://github.com/westpa/westpa/actions/runs/20641223356

All Python 3.14 tests began to hang on the `TestInstantiations/test_zeroMQ` test from `test_work_managers/test_environment.py`. This is due to the fact that the zeromq work manager is not properly handling the `ValueError` raised by `numpy 2.4.0` for inplace numpy resizing.



Since inplace resizing will (seemingly) be removed in the future anyways, we might as well just forgo that completely. This will increase memory usage, but that's what numpy wants.

I think overall we need to fix zeromq so the futures will handle the errors more elegantly. You can throw in a `raise ValueError`  in the [add_timer() method in src/westpa/work_managers/zeromq/core.py](https://github.com/westpa/westpa/blob/westpa2/src/westpa/work_managers/zeromq/core.py#L208) and it will hang similarly in any python version (tried it on Python 3.13, both numpy 2.3.5, 2.4.0). That'll require some more digging so I'll leave it to a different PR.


Hang can be reproduced via the following on python 3.14/numpy 2.4.0:
```
pytest -v tests/test_work_managers/test_environment.py -k 'testZeroMQ' 
```


## Goals and Outstanding Issues
<!--- A clear and concise list of goals (to be) accomplished. --->
- [x] Make Python 3.14 tests run

## Major files changed
<!--- Manually list files or include a diff link in the form of: https://github.com/user/westpa/compare/<initial SHA>..<final SHA> --->
- [x] src/westpa/work_managers/zeromq/core.py

## Status
<!--- Delete bullet points that are not relevant. --->
- [x] Bug fix (non-breaking change which fixes an issue)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [x] My change requires a change to the documentation.
- [x] I have updated the documentation accordingly.
- [x] I have added tests to cover my changes.
- [x] All new and existing tests passed.

## Additional context
<!--- Add any other context or screenshots about the pull request here. --->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `96a0573dd421`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.