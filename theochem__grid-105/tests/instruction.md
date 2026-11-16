# Issue

**Title:** Rename Sub to Local, to better reflect code behavior

## Description

.

The function get_subgrid can return larger grids than the original one in case of periodic grids, typically when the cutoff sphere contains multiple unit cells. The resulting grid is therefore not necessarily a "sub"grid. This function does always make a local grid, centered around some piont, making "local"grid is more appropriate.

In some cases, the term subgrid was used in another context, e.g. for an atomic grid in a molecular grid. These were not renamed.

At the momemt, the following renamings were done:

- `subgrid` -> `localgrid`
- `subfn` -> `localfn`
- `SubGrid` -> `SubGrid`

and a few variants of these. One could argue that the first two would look better with an underscore after `local`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1a44a23d1d54`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.