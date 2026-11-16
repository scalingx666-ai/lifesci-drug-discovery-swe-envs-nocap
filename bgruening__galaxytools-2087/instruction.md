# Issue

**Title:** Add 3Dtrees: Raster 1.0.0

## Description

FOR CONTRIBUTOR:
* [x] I have read the [CONTRIBUTING.md](https://github.com/galaxyproject/tools-iuc/blob/master/CONTRIBUTING.md) document and this tool is appropriate for the tools-iuc repo.
* [x] License permits unrestricted use (educational + commercial)
* [x] This PR adds a new tool or tool collection
* [ ] This PR updates an existing tool or tool collection
* [ ] This PR does something else (explain below)

Adds **3Dtrees: Raster 1.0.0** (`tools/3dtrees_raster`), container `ghcr.io/3dtrees-earth/3dtrees_raster:1.0.0` ([release](https://github.com/3dTrees-earth/3Dtrees_Raster/releases/tag/v1.0.0)).

From one segmented LAS/LAZ or COPC point cloud the tool writes:
- tile metrics of forest structure and per-segment diagnostics (CSV), and the tile polygons (GeoJSON), for each instance dimension (`PredInstance`, `_SAT`, `_FM`, `_RCT`);
- DTM, CHM, DSM and gap-filled CHM as Cloud Optimized GeoTIFFs;
- voxel point counts as CSV, multiband GeoTIFF and a COPC point cloud.

Optional: an area of interest, and a kNN distance noise filter (k = 8, mean + 2σ over the whole cloud; off by default).

- `planemo lint --report_level all`: clean.
- `planemo test --docker` (run as a normal user): 4/4 tests pass. They cover COPC and plain LAZ input, the area of interest, the filter on and off, and the advanced parameters.

After merge: install on Galaxy EU. The tool then becomes the raster step of the 3Dtrees workflow.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `39ce1f0f30d9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.