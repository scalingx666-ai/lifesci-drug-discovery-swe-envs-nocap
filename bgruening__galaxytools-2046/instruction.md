# Issue

**Title:** Update 3Dtrees: Smart Tile v2.4.1

## Description

<!-- claude-projects-attribution: {"github_login":"kgerb"} -->
_Requested by **Kilian**_

FOR CONTRIBUTOR:
* [x] I have read the [CONTRIBUTING.md](https://github.com/galaxyproject/tools-iuc/blob/master/CONTRIBUTING.md) document and this tool is appropriate for the tools-iuc repo.
* [x] License permits unrestricted use (educational + commercial)
* [ ] This PR adds a new tool or tool collection
* [x] This PR updates an existing tool or tool collection
* [ ] This PR does something else (explain below)

Updates `3dtrees_smart_tile` to **2.4.1+galaxy0** with container `ghcr.io/3dtrees-earth/3dtrees_smart_tile:2.4.1` ([SmartTile v2.4.1](https://github.com/3dTrees-earth/3dtrees_Smart_Tile/releases/tag/v2.4.1)). Remap can now take RayCloudTools tree tables.

**Why 2.4.1:** the first `:2.4.0` image failed on Galaxy EU. Every remap, and every Filter / merge writing into the original files, failed with `[Errno 16] Device or resource busy: '.../.enrich-...'`: scratch files were still open when their folder was removed on the NFS job directories. The fix was released by rebuilding `:2.4.0` in place, but the EU compute nodes keep the old image cached by tag, and reruns there still failed. 2.4.1 is the fixed code under a new tag, so every node fetches it. It also accepts RayCloudTools tiles without trees.

**Changes**
- Version 2.4.1, so the container is `:2.4.1`.
- **Remap → RayCloudTools tree tables (No / Yes):** with Yes, one collection takes the *Tree tables* output of Filter / merge (RayCloudTools model): tree tables, tree info tables and meshes together. The command routes each element into `--tree-tables-folder`, `--tree-info-folder` or `--tree-meshes-folder` by format and name, and SmartTile pairs them with the merged tiles by tile name.
- **New output *Tree tables of the originals*:** each original's tree table, tree info table and mesh (`<original>_trees`, `_trees_info`, `_trees_mesh`). It is produced by Remap with RayCloudTools tree tables, and by Filter / merge with the RayCloudTools model and the original files as target.
- Two tests, with four small fixtures produced by SmartTile 2.4.1 from the existing RayCloudTools test data:
  - Remap with RayCloudTools tree tables.
  - Filter / merge with the RayCloudTools model onto the original files.
- One help sentence for the new remap option.

**Tests**
- `planemo lint --fail_level warn` is clean.
- `planemo test`: 9/9 passed (7 existing + 2 new) in a local Galaxy `release_25.1` with Docker and `ghcr.io/3dtrees-earth/3dtrees_smart_tile:2.4.1`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `155bd58df953`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.