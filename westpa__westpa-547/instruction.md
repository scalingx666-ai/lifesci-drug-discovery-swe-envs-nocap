# Issue

**Title:** Pyproject.toml licensefile fix

## Description

## Issue Number
<!--- Is this pull request related to any outstanding issues? If so, list the issue number. --->


## Describe the changes made
<!--- A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it. -->
When running pip install with the `-v` flag, the verbose log indicates that it could not find the correct LICENSE file, despite us having one. It's because there is an extra `.` in the [pattern we provided](https://github.com/westpa/westpa/blob/westpa2/pyproject.toml#L23) (our license file has no file extension). Leaving this bug around will break project building from March 20, 2026 onwards, per the deprecation warning.

BEFORE fix:
```
  Running command Building wheel for westpa (pyproject.toml)
  /private/var/folders/06/29rlbptd5jq_rfl__96vd2qh0000gn/T/pip-build-env-0sku5q76/overlay/lib/python3.12/site-packages/setuptools/dist.py:483: SetuptoolsDeprecationWarning: Cannot find any files for the given pattern.
  !!

          ********************************************************************************
          Pattern 'LICEN[CS]E.*' did not match any files.

          By 2026-Mar-20, you need to update your project and remove deprecated calls
          or your builds will no longer be supported.
          ********************************************************************************

  !!
    for path in sorted(cls._find_pattern(pattern, enforce_match))
```

AFTER fix:
```
  adding license file 'LICENSE'
```


## Goals and Outstanding Issues
<!--- A clear and concise list of goals (to be) accomplished. --->
- [x] Fix deprecated call/typo in pyproject.toml

## Major files changed
<!--- Manually list files or include a diff link in the form of: https://github.com/user/westpa/compare/<initial SHA>..<final SHA> --->
- [x] pyproject.toml

## Status
<!--- Delete bullet points that are not relevant. --->
- [x] Bug fix (non-breaking change which fixes an issue)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [x] All new and existing tests passed.

## Additional context
<!--- Add any other context or screenshots about the pull request here. --->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e5f3a6dc3fb8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.