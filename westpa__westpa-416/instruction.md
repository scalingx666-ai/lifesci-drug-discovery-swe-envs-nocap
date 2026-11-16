# Issue

**Title:** Suppress NaturalNameWarning when using HDF5 Framework

## Description

## Issue Number
<!--- Is this pull request related to any outstanding issues? If so, list the issue number. --->


## Describe the changes made
<!--- A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it. -->
Depending on the verbosity, ``Pytables`` raises ``NaturalNameWarning`` when we use the HDF5 Framework because some of our datasets/nodes are name like ``0_0`` (or the format ``<iteration>_<stateid>``). This PR suppresses such error because it's not helpful.

## Goals and Outstanding Issues
<!--- A clear and concise list of goals (to be) accomplished. --->
- [x] Silent common NaturalNameWarning from PyTables (via mdtraj)

## Major files changed
<!--- Manually list files or include a diff link in the form of: https://github.com/user/westpa/compare/<initial SHA>..<final SHA> --->
- [x] src/westpa/core/h5io.py

## Status
<!--- Delete bullet points that are not relevant. --->
- [x] Bug fix (non-breaking change which fixes an issue)
- [x] New feature (non-breaking change which adds functionality)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [x] All new and existing tests passed.

## Additional context
<!--- Add any other context or screenshots about the pull request here. --->

```
/usr/local/lib/python3.10/dist-packages/tables/path.py:137: NaturalNameWarning: object name is not a valid Python identifier: '0_12'; it does not match the pattern ``^[a-zA-Z_][a-zA-Z0-9_]*$``; you will not be able to use natural naming to access this object; using ``getattr()`` will still work, though
  check_attribute_name(name)
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `05f5cd61390c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.