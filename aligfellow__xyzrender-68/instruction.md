# Issue

**Title:** Fast fail

## Description

Error out earlier if the input file is invalid. This actually saves a lot of wasted time if you make a typo.

Example: `hat_S_dens.cube1` (does not exist) is typed when `hat_S_dens.cube` is the intended file.
 `time uv run xyzrender --dens hat_S_dens.cube1 --hy -o hat_dens.svg`
Currently (on my laptop):
11.378s (more time than it takes to actually read the real cube file and render the svg!!)

With these commits:
3.213s

Note: No actual work is done in either of these cases, since the `.cube1` file does not exist, and is not a recognized extension, so the contents of the cube file are irrelevant.

The program currently tries to use `cclib` as a fallback for reading the input, but to no avail.

The second commit moves some imports to after we verify the input file exists. Without this commit the time to fail is ~6 seconds instead of 3.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2c2aae34b171`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.