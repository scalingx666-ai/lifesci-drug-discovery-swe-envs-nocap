# Issue

**Title:** Fix cibuildwheel for macOS/Python 3.14

## Description

## Issue Number
<!--- Is this pull request related to any outstanding issues? If so, list the issue number. --->


## Describe the changes made
<!--- A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it. -->
Brew (the macOS package manager) recently updated their hdf5 bottle to 2.0.0 and that is seemingly broke the macOS Python 3.14 wheel testing.

```
    File "/private/var/folders/yz/zr09txvs5dn18vt4cn21kzl40000gn/T/cibw-run-tklpmp64/cp314-macosx_universal2/venv-test-x86_64/lib/python3.14/site-packages/tables/file.py", line 27, in <module>
      from . import (
      ...<6 lines>...
      )
  ImportError: dlopen(/private/var/folders/yz/zr09txvs5dn18vt4cn21kzl40000gn/T/cibw-run-tklpmp64/cp314-macosx_universal2/venv-test-x86_64/lib/python3.14/site-packages/tables/hdf5extension.abi3.so, 0x0002): symbol not found in flat namespace '_H5Dread_chunk1'
```
It's seemingly related to how a arm64 install of hdf5 doesn't work during testing in a x86_64 `venv`. This PR basically separates out the wheels for arm64 and x86_64 for the macOS/Python 3.14 config.

https://github.com/jeremyleung521/westpa/actions/runs/21606536930

## Goals and Outstanding Issues
<!--- A clear and concise list of goals (to be) accomplished. --->
- [x] Fix cibuildwheel for macOS/Python 3.14

## Major files changed
<!--- Manually list files or include a diff link in the form of: https://github.com/user/westpa/compare/<initial SHA>..<final SHA> --->
- [x] .github/workflows/build.yaml

## Status
<!--- Delete bullet points that are not relevant. --->
- [x] Bug fix (non-breaking change which fixes an issue)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [x] All new and existing tests passed.

## Additional context
<!--- Add any other context or screenshots about the pull request here. --->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d4fc6b0b6597`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.