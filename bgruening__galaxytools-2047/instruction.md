# Issue

**Title:** Update 3Dtrees: RayCloudTools 1.2.3

## Description

<!-- claude-projects-attribution: {"github_login":"kgerb"} -->
_Requested by **Kilian**_

FOR CONTRIBUTOR:
* [x] I have read the [CONTRIBUTING.md](https://github.com/galaxyproject/tools-iuc/blob/master/CONTRIBUTING.md) document and this tool is appropriate for the tools-iuc repo.
* [x] License permits unrestricted use (educational + commercial)
* [ ] This PR adds a new tool or tool collection
* [x] This PR updates an existing tool or tool collection
* [ ] This PR does something else (explain below)

Updates `3dtrees_raycloudtools` to **1.2.3+galaxy0** with container `ghcr.io/3dtrees-earth/3dtrees_rct:1.2.3` ([RCT v1.2.3](https://github.com/3dTrees-earth/3dTrees_RCT/releases/tag/v1.2.3)).

**Why:** with tree info, RCT 1.2.2 fails on any tile without trees: `FileNotFoundError: 'out/input_trees_info.txt'`, because treeinfo cannot run without trees. On Galaxy EU this was a ground-only edge tile (job 4838ba20a6d86765e08a6981dc0a235d) of a 4-file dataset tiled for RayCloudTools. That one failed element stopped the whole collection before SmartTile Filter / merge. With 1.2.3 such a tile finishes:
- `PredInstance_RCT` is 0 for every point.
- The tree table and tree info table are header only.
- The tree mesh has the header and no vertices or faces.

So every output exists for every tile, and SmartTile 2.4.1 (#2046) accepts them.

**Changes**
- Version 1.2.3+galaxy0, so the container is `:1.2.3`. The command and inputs are unchanged.
- New test on `ground`, a 16,353-point (73 KB) ground-only crop of that Galaxy EU tile. It checks all four tree outputs: the segmented LAZ, the header-only tables (2 lines each), and the mesh with `rct_tree_count 0`, `element vertex 0` and `element face 0`.
- The test-data README describes the fixture.

**Tests**
- `planemo lint --fail_level warn` is clean.
- `planemo test`: 4/4 passed (3 existing + 1 new) in a local Galaxy `release_25.1` with Docker and `ghcr.io/3dtrees-earth/3dtrees_rct:1.2.3`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `155bd58df953`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.