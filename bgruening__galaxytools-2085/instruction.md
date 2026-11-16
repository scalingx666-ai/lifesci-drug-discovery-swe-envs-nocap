# Issue

**Title:** Update 3Dtrees: SmartTile v2.4.2

## Description

<!-- claude-projects-attribution: {"github_login":"kgerb"} -->
_Requested by **Kilian**_

FOR CONTRIBUTOR:
* [x] I have read the [CONTRIBUTING.md](https://github.com/galaxyproject/tools-iuc/blob/master/CONTRIBUTING.md) document and this tool is appropriate for the tools-iuc repo.
* [x] License permits unrestricted use (educational + commercial)
* [ ] This PR adds a new tool or tool collection
* [x] This PR updates an existing tool or tool collection
* [ ] This PR does something else (explain below)

Updates `3dtrees_smart_tile` to **2.4.2+galaxy0**, with container `ghcr.io/3dtrees-earth/3dtrees_smart_tile:2.4.2` ([SmartTile v2.4.2](https://github.com/3dTrees-earth/3dtrees_Smart_Tile/releases/tag/v2.4.2), image digest `sha256:d5d67125644f343c8b24abc098b032d8f808bd32bd9410eb67bc8e1e04519e9b`).

**Changes**
- `@TOOL_VERSION@` 2.4.1 → 2.4.2; `@VERSION_SUFFIX@` stays 0. No other wrapper change.

**What 2.4.2 fixes**
- Float ExtraBytes with a scale and no_data 0 (RIEGL Amplitude/Reflectance after standardization) no longer stop `create_merged_file` and `remap`.
- Every ExtraBytes name survives PDAL/untwine. A column named like a standard LAS field comes out as `<name>_extra`.
- Merge and remap accept RayCloudTools terrain meshes (`--terrain-meshes-folder`). The wrapper does not expose this yet.
- Native threads stay within `--workers` (`${GALAXY_SLOTS}`).

**Tests**
- `planemo lint --fail_level warn` is clean.
- `planemo test`: 9/9 passed in a local Galaxy `release_25.1` with Docker and the `:2.4.2` image.

**After merge**
- Install 2.4.2 on Galaxy EU.
- Then update the 3Dtrees production workflows to `3dtrees_smart_tile/2.4.2+galaxy0`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6cdd8587827f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.