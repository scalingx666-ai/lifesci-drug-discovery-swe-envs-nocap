# Issue

**Title:** Update 3Dtrees: Smart Tile v2.4

## Description

<!-- claude-projects-attribution: {"github_login":"kgerb"} -->
_Requested by **Kilian** · [project thread](https://claude.ai/code/project/chan_01DMg1jiAvtyYXCxTqevHXvC?thread=cmsg_01DMg1jiAvtyYXCxTqevHXvCQHmZnxYzFEwZ1vEbXPmzt8)_

FOR CONTRIBUTOR:
* [x] I have read the [CONTRIBUTING.md](https://github.com/galaxyproject/tools-iuc/blob/master/CONTRIBUTING.md) document and this tool is appropriate for the tools-iuc repo.
* [x] License permits unrestricted use (educational + commercial)
* [ ] This PR adds a new tool or tool collection
* [x] This PR updates an existing tool or tool collection
* [ ] This PR does something else (explain below)

Updates `3dtrees_smart_tile` from 2.3 to **2.4.0+galaxy0**, wrapping [SmartTile release v2.4.0](https://github.com/3dTrees-earth/3dtrees_Smart_Tile/releases/tag/v2.4.0) (`ghcr.io/3dtrees-earth/3dtrees_smart_tile:2.4.0`). It replaces the closed #2026. The RayCloudTools wrapper update it relies on for workflows is in #2031.

**Changes**
- **Tile:** up to three outputs. Each is subsampled or at the original resolution, as LAZ, COPC LAZ or PLY. Choose buffered spatial tiles, or tiles in which every existing tree stays whole (with extra attributes kept) for species prediction per tree.
- **Filter / merge:** segmented tiles as a collection, with their voxel size.
  - *Remap target*: subsampled tiles (the predictions are transferred onto them first), the original files (returned with the predictions), or none (filter at the segmented voxel size).
  - Ownership anchor, cross-tile reconciliation and small-cluster reassignment are under *Advanced options*.
  - RayCloudTools takes the *Tree-file*, *Tree-file incl. treeinfo* and *Tree-mesh* (when *Tree meshes* is Yes) collections as RayCloudTools produces them in a workflow, named like the tile. They are linked as `<tile>_trees.txt`, `<tile>_trees_info.txt` and `<tile>_trees_mesh.ply`.
- **Remap:** one or more prediction collections, with an optional dimension allowlist. Predictions can be subsampled or at the original resolution. Also adds a custom instance field, *Match within the same existing instance*, and an optional merged file.
- **Create merged file:** joins several collections of the same originals (e.g. after SAT and ForestMamba remap) into one LAZ, COPC LAZ or PLY file. Full resolution can add `OriginalPointIndex` for ForestStructure.
- **Output names** have no file extension (e.g. `mikro_subsampled_10cm`, `c00_r00`, `prod_merged_10cm`), so tools that add the datatype extension never stage `x.laz.laz`. Inputs are linked as `<name without extension>.<datatype extension>`.
- **Every file input** is a required dataset or collection picker. The optional cases are choices instead (Remap target *None*, RayCloudTools *Tree meshes* Yes/No), so Galaxy never shows a plain "Nothing selected" dropdown for files.
- **Merged files** go to one collection per format: *Merged LAZ*, *Merged COPC LAZ* and *Merged PLY*. Each is created only when that format is selected (COPC LAZ is preselected).
- Removes the 2.3 flags that SmartTile 2.4 rejects. Threads follow `GALAXY_SLOTS`. Each task is one plain command block.
- The help has three workflow figures (`static/images`). The ToolShed description no longer names a version.

**Tests**
Seven tests, each checking output content:
- tile at 1 cm COPC and 10 cm LAZ;
- whole-instance tiles at original resolution;
- Filter / merge onto 1 cm tiles;
- Filter / merge onto the original files;
- Filter / merge of RayCloudTools tiles with workflow-named tables and a mesh;
- Remap of species within the same tree with a full-resolution PLY;
- Create merged file from two collections.

**Validation**
- `planemo lint --fail_level warn` is clean.
- `planemo test`: 7/7 passed in a local Galaxy 25.1 with Docker and the published `ghcr.io/3dtrees-earth/3dtrees_smart_tile:2.4.0` image (digest `sha256:7ddbca77e031…`). A Create merged file run with LAZ, COPC LAZ and PLY produced exactly the three per-format collections.
- End-to-end with RayCloudTools 1.2.2+galaxy1 (#2031), as in a workflow: Tile → RayCloudTools with tree info, mapped over the 10 cm tiles → Filter / merge (RayCloudTools model) with the four RayCloudTools collections as they come. That returned the merged tile plus the filtered tree table, tree info table and mesh.

The tool runs in the Docker container above; it has no conda package, as in 2.3.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `19a59bad8913`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.