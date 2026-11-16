# Issue

**Title:** `which_import` now handles submodules correctly

## Description

## Description

<strike>For checking if OpenMM exists in the environment, we need to feed
"simtk.openmm" to `importlib.util.find_spec`. This will work by actually
importing `simtk`, which in the case of OpenMM not being present raises
a `ModuleNotFoundError`.

This PR handles the case in which this `ModuleNotFoundError` is raised.</strike>

For checking if OpenMM exists in the environment, we need to feed "openmm" with `package="simtk"` to `importlib.util.find_spec`. This PR adds a new keyword arg `package` to `which_import` in order to pass this through to `find_spec`.

## Status
- [ ] Changelog updated
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b4e814512255`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.