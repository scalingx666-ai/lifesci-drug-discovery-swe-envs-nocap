# Issue

**Title:** Fixed several bugs an nuisances in cathub organize script

## Description

Here are a bunch of fixes that give people trying to upload their data a hard time. Specifically:

- standard energy window for recognized reaction energies is raised from +/-10 eV to +/-100 eV
- CLI flags show default in help page. Can't really think of any reasons when this should not be shown.
- `cathub organize` now has additional optional flag `-d` or `--gas-dir` to include additional directory for gas phase references. Saves the user from copying gas phase molecules around. This is really only a UI enhancement but still handy
- the use of the `*.cache.pckl` file is now optional and off by default because more often than not it would confuse user when not deleted. It can still be useful for accelerating multiple runs from the same set of large (say OUTCAR) files with `-u` or `--use-cache`
- when `cathub organize` does not specify facet `-f` the script will try to glean Miller indices from path: but now it will also name the folder accordingly.

That's it. Would be nice if it could make its way into CatKit (& suncat & sherlock cluster soon).

Thanks and have nice weekend.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e6f0d60fb08d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.