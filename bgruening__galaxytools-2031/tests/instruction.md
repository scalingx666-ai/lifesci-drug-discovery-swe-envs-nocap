# Issue

**Title:** Update 3Dtrees: RayCloudTools 1.2.2+galaxy1

## Description

<!-- claude-projects-attribution: {"github_login":"kgerb"} -->
_Requested by **Kilian** · [project thread](https://claude.ai/code/project/chan_01DMg1jiAvtyYXCxTqevHXvC?thread=cmsg_01DMg1jiAvtyYXCxTqevHXvCQHmZnxYzFEwZ1vEbXPmzt8)_

FOR CONTRIBUTOR:
* [x] I have read the [CONTRIBUTING.md](https://github.com/galaxyproject/tools-iuc/blob/master/CONTRIBUTING.md) document and this tool is appropriate for the tools-iuc repo.
* [x] License permits unrestricted use (educational + commercial)
* [ ] This PR adds a new tool or tool collection
* [x] This PR updates an existing tool or tool collection
* [ ] This PR does something else (explain below)

Updates `3dtrees_raycloudtools` to **1.2.2+galaxy1**, with the same container (`ghcr.io/3dtrees-earth/3dtrees_rct:1.2.2`). The changes let the RayCloudTools outputs feed SmartTile Filter / merge (#2029) in a workflow.

**Changes**
- The *Tree-file* (`tree_model_txt`) is now always returned, also when tree info is requested. Before, it was dropped whenever *Tree-file incl. treeinfo* was produced, but SmartTile needs both tables.
- The input is staged under the fixed internal name `input.laz`. py_rct's `treeinfo` derives the info file name from the first dot (`tree_file.split('.')[0] + '_info.txt'`), which failed for any input name containing a dot, e.g. a SmartTile tile named `mikro_subsampled_10cm.laz`. The tests passed only because their input is named `mikro`. Galaxy still names every output after the input's element identifier, so workflows keep the link to the original tile.
- The tree-info tests now expect five outputs.

**Tests**
- `planemo lint --fail_level warn` is clean.
- `planemo test`: 3/3 passed in a local Galaxy 25.1 with Docker and `ghcr.io/3dtrees-earth/3dtrees_rct:1.2.2`.
- A collection element named `plot.2024 a.laz` (dots, space and extension) ran with tree info. All five outputs kept the element name `plot.2024 a.laz`.
- End-to-end in the same Galaxy:
  1. SmartTile Tile on `mikro` at 10 cm and 1 cm.
  2. This tool with tree info, mapped over the 10 cm tile collection.
  3. Its four output collections, named like the tile, fed straight into SmartTile Filter / merge (RayCloudTools model).
  - Result: the merged tile plus the filtered tree table, tree info table and mesh, with tile-based tree IDs.

The root cause in py_rct should also be fixed (derive the info file from the full name). This wrapper change keeps working either way.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `19a59bad8913`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.