# Issue

**Title:** render_gif: load input once, keep charge for gif_trj

## Description

- Load the input once instead of re-reading it for the rot/diffuse/trj branches.
- `gif_trj` now passes the file's (or CLI `-c`/`-m`) charge and multiplicity to the trajectory builder; previously always charge 0.
- Path input keeps its cell data for `gif_rot` (the cell box was dropped before).
- `overlay` + `mo`/`dens` and `ref` on periodic structures now raise, matching `render()` (both were broken in GIFs before).

Overlaps with #178 in `render_gif`; one of the two will need a rebase.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `53be3dd61ac5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.