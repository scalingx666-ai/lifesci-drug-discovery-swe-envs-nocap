# Issue

**Title:** Add 3Dtrees: Sidecar 0.1.0

## Description

<!-- claude-projects-attribution: {"github_login":"kgerb"} -->
_Requested by **Kilian**_

FOR CONTRIBUTOR:
* [x] I have read the [CONTRIBUTING.md](https://github.com/galaxyproject/tools-iuc/blob/master/CONTRIBUTING.md) document and this tool is appropriate for the tools-iuc repo.
* [x] License permits unrestricted use (educational + commercial)
* [x] This PR adds a new tool or tool collection
* [ ] This PR updates an existing tool or tool collection
* [ ] This PR does something else (explain below)

Adds `3dtrees_sidecar` **0.1.0+galaxy0**. It uses the container `ghcr.io/3dtrees-earth/3dtrees_sidecar:0.1.0` from [3dTrees-earth/3dtrees_sidecar](https://github.com/3dTrees-earth/3dtrees_sidecar).

The tool stores a method's per-point results apart from the point cloud and builds downloadable point clouds from them. It is one tool with a *Task* select, like 3Dtrees: SmartTile:

- **Export**: takes one method result (LAZ) and *Columns to keep*. It writes a Parquet *sidecar* with `point_index` plus only those columns. Columns that are not kept are named as a warning.
- **Assemble**: takes the standardized LAZ and any number of *Sidecar* entries, from any method. It writes the download LAZ: every standard field unchanged and in order, plus the sidecars' columns.
- **Check**: rebuilds the download from the same inputs and compares it value by value with a stored one.

Every task writes a JSON report (identity, point count, columns, SHA-256 hashes). One job handles one item. Map the tool over collections whose element identifiers are the dataset item ids. Assemble refuses a sidecar from another item or generation, so mispaired collections fail.

**Draft: blocked on the container.** The wrapper needs the tool code merged in  (merged, `3161578`). The published `ghcr.io/3dtrees-earth/3dtrees_sidecar:0.1.0` is still the earlier build (`sha256:b1538457…`), whose `export` requires `--base`. With that image, the export tests here fail. This PR is ready for review once the image is republished from `main`, or released under a new version and pinned here.

**Tests** (run against a local image built from `3161578`)
- `planemo lint --fail_level warn` is clean.
- `planemo test`: 10/10 passed in a local Galaxy `release_25.1` with Docker. The tests cover export (incl. the not-kept warning), assemble with none, one or two sidecars, check, and the refusal cases.
- Collections in the same Galaxy:
  - Three synthetic items as list collections: export, assemble and check 3/3 green each.
  - A reversed sidecar list was refused for the mispaired items.
- Real data:
  - Input: three standardized ULS files (SIRGAS 2000 / UTM 23S), cropped to a shared 30 × 30 m box: 1.19 M, 1.45 M and 0.22 M points.
  - Path: SmartTile tile → RayCloudTools 1.2.2 → SmartTile merge to the original files → export (`PredInstance_RCT`) → assemble → check. All green.
  - laspy confirms that each download keeps every standard field, the header and the CRS of its standardized file, and that `PredInstance_RCT` matches the RayCloudTools result.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `392432b1d5f0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.